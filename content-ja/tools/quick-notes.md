---
title: "クイックメモ帳"
date: 2025-05-16
description: "無料のオンラインメモ帳。書いた内容はブラウザに自動保存。複数メモ・検索・ダウンロード対応。会員登録不要・オフラインでも動作。"
categories: ["無料ツール"]
tags: ["オンラインメモ帳", "クイックメモ", "メモ帳", "自動保存", "ブラウザメモ", "オフライン", "生産性ツール"]
slug: "quick-notes"
cover:
  image: "/images/covers/quick-notes-ja.png"
  alt: "クイックメモ帳 - 無料オンラインメモ"
ShowToc: false
---

<div id="qn-app">

<style>
/* ── Reset & Root ─────────────────────────────────────── */
#qn-app {
  font-family: 'Helvetica Neue', Arial, 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', Meiryo, sans-serif;
  max-width: 1100px;
  margin: 0 auto;
  color: #1e1b4b;
  --accent: #7c3aed;
  --accent-dk: #6d28d9;
  --accent-lt: #ede9fe;
  --bg: #f8f7ff;
  --surface: #ffffff;
  --border: #d8d3f0;
  --text: #1e1b4b;
  --text-muted: #6b7280;
  --sidebar-bg: #f5f3ff;
  --textarea-bg: #fafafe;
  --status-bg: #f3f0ff;
  --btn-ghost: #ede9fe;
  --btn-ghost-text: #5b21b6;
  --shadow: 0 2px 12px rgba(124,58,237,0.10);
  --radius: 10px;
  --danger: #dc2626;
  --danger-lt: #fee2e2;
  --success: #059669;
}
#qn-app * { box-sizing: border-box; }

/* ── Dark theme ───────────────────────────────────────── */
#qn-app.qn-dark {
  --bg: #0f0e1a;
  --surface: #1a1828;
  --border: #3b3660;
  --text: #e5e1ff;
  --text-muted: #9d97c4;
  --sidebar-bg: #13111f;
  --textarea-bg: #15132a;
  --status-bg: #1a1828;
  --btn-ghost: #2a2540;
  --btn-ghost-text: #c4b5fd;
  --shadow: 0 2px 12px rgba(0,0,0,0.40);
  color: var(--text);
}

/* ── Layout ───────────────────────────────────────────── */
#qn-app .qn-wrap {
  background: var(--bg);
  border-radius: var(--radius);
  border: 1px solid var(--border);
  overflow: hidden;
  box-shadow: var(--shadow);
  display: flex;
  flex-direction: column;
  min-height: 600px;
}
#qn-app .qn-toolbar {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 8px 12px;
  background: var(--surface);
  border-bottom: 1px solid var(--border);
  flex-wrap: wrap;
}
#qn-app .qn-body {
  display: flex;
  flex: 1;
  min-height: 0;
}
#qn-app .qn-sidebar {
  width: 220px;
  min-width: 180px;
  background: var(--sidebar-bg);
  border-right: 1px solid var(--border);
  display: flex;
  flex-direction: column;
  overflow: hidden;
}
#qn-app .qn-search-wrap {
  padding: 8px;
  border-bottom: 1px solid var(--border);
}
#qn-app .qn-search {
  width: 100%;
  padding: 6px 10px;
  border: 1px solid var(--border);
  border-radius: 6px;
  background: var(--surface);
  color: var(--text);
  font-size: 13px;
  outline: none;
}
#qn-app .qn-search:focus { border-color: var(--accent); }
#qn-app .qn-note-list {
  flex: 1;
  overflow-y: auto;
  padding: 4px;
}
#qn-app .qn-note-item {
  padding: 8px 10px;
  border-radius: 7px;
  cursor: pointer;
  margin-bottom: 2px;
  transition: background 0.15s;
  border: 1px solid transparent;
  position: relative;
}
#qn-app .qn-note-item:hover { background: var(--btn-ghost); }
#qn-app .qn-note-item.active {
  background: var(--accent-lt);
  border-color: var(--accent);
}
#qn-app.qn-dark .qn-note-item.active { background: var(--btn-ghost); }
#qn-app .qn-note-title {
  font-size: 13px;
  font-weight: 600;
  color: var(--text);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 150px;
}
#qn-app .qn-note-preview {
  font-size: 11px;
  color: var(--text-muted);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 160px;
  margin-top: 2px;
}
#qn-app .qn-note-del {
  position: absolute;
  top: 6px;
  right: 6px;
  background: none;
  border: none;
  color: var(--text-muted);
  cursor: pointer;
  font-size: 14px;
  line-height: 1;
  padding: 2px 4px;
  border-radius: 4px;
  opacity: 0;
  transition: opacity 0.15s;
}
#qn-app .qn-note-item:hover .qn-note-del { opacity: 1; }
#qn-app .qn-note-del:hover { color: var(--danger); background: var(--danger-lt); }
#qn-app .qn-sidebar-footer {
  padding: 8px;
  border-top: 1px solid var(--border);
}
#qn-app .qn-new-btn {
  width: 100%;
  padding: 8px;
  background: var(--accent);
  color: #fff;
  border: none;
  border-radius: 7px;
  cursor: pointer;
  font-size: 13px;
  font-weight: 600;
  transition: background 0.15s;
}
#qn-app .qn-new-btn:hover { background: var(--accent-dk); }

/* ── Editor pane ──────────────────────────────────────── */
#qn-app .qn-editor-pane {
  flex: 1;
  display: flex;
  flex-direction: column;
  background: var(--surface);
  min-width: 0;
}
#qn-app .qn-title-bar {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px 12px;
  border-bottom: 1px solid var(--border);
  background: var(--surface);
}
#qn-app .qn-note-name-input {
  flex: 1;
  border: 1px solid transparent;
  background: transparent;
  color: var(--text);
  font-size: 15px;
  font-weight: 700;
  padding: 4px 8px;
  border-radius: 6px;
  outline: none;
  transition: border-color 0.15s;
  font-family: inherit;
}
#qn-app .qn-note-name-input:focus {
  border-color: var(--accent);
  background: var(--textarea-bg);
}
#qn-app .qn-textarea {
  flex: 1;
  width: 100%;
  border: none;
  outline: none;
  resize: none;
  padding: 16px 20px;
  font-size: 15px;
  line-height: 1.9;
  background: var(--textarea-bg);
  color: var(--text);
  font-family: inherit;
  min-height: 420px;
}
#qn-app .qn-textarea::placeholder { color: var(--text-muted); }

/* ── Status bar ───────────────────────────────────────── */
#qn-app .qn-status {
  display: flex;
  align-items: center;
  gap: 14px;
  padding: 6px 14px;
  background: var(--status-bg);
  border-top: 1px solid var(--border);
  font-size: 12px;
  color: var(--text-muted);
  flex-wrap: wrap;
}
#qn-app .qn-status .qn-saved {
  margin-left: auto;
  color: var(--success);
  font-weight: 600;
  font-size: 11px;
  transition: opacity 0.4s;
}
#qn-app .qn-status .qn-saved.hidden { opacity: 0; }

/* ── Toolbar buttons ──────────────────────────────────── */
#qn-app .qn-btn {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 5px 11px;
  border-radius: 6px;
  border: 1px solid var(--border);
  background: var(--btn-ghost);
  color: var(--btn-ghost-text);
  cursor: pointer;
  font-size: 13px;
  font-weight: 500;
  transition: background 0.15s, border-color 0.15s;
  white-space: nowrap;
  font-family: inherit;
}
#qn-app .qn-btn:hover { background: var(--accent-lt); border-color: var(--accent); color: var(--accent-dk); }
#qn-app .qn-btn-primary {
  background: var(--accent);
  color: #fff;
  border-color: var(--accent);
}
#qn-app .qn-btn-primary:hover { background: var(--accent-dk); border-color: var(--accent-dk); color: #fff; }
#qn-app .qn-spacer { flex: 1; }

/* ── Search highlight ─────────────────────────────────── */
#qn-app .qn-highlight { background: #fde68a; border-radius: 2px; }

/* ── Empty state ──────────────────────────────────────── */
#qn-app .qn-empty {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 12px;
  color: var(--text-muted);
  padding: 40px;
  text-align: center;
}
#qn-app .qn-empty svg { opacity: 0.3; }
#qn-app .qn-empty p { font-size: 15px; margin: 0; }

/* ── freee CTA ────────────────────────────────────────── */
#qn-freee-cta {
  margin-top: 28px;
  padding: 18px 20px;
  background: var(--accent-lt, #ede9fe);
  border: 1px solid var(--border, #d8d3f0);
  border-radius: var(--radius, 10px);
  font-size: 14px;
  line-height: 1.7;
  color: var(--text, #1e1b4b);
}
#qn-freee-cta strong { color: var(--accent, #7c3aed); }
#qn-freee-cta a.qn-freee-link {
  display: inline-block;
  margin-top: 10px;
  padding: 8px 20px;
  background: var(--accent, #7c3aed);
  color: #fff;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 600;
  font-size: 13px;
  transition: background 0.15s;
}
#qn-freee-cta a.qn-freee-link:hover { background: var(--accent-dk, #6d28d9); }

/* ── Related ──────────────────────────────────────────── */
#qn-related {
  margin-top: 16px;
  font-size: 13px;
  color: var(--text-muted, #6b7280);
}
#qn-related a { color: var(--accent, #7c3aed); text-decoration: none; }
#qn-related a:hover { text-decoration: underline; }

/* ── Responsive ───────────────────────────────────────── */
@media (max-width: 640px) {
  #qn-app .qn-sidebar { width: 160px; min-width: 140px; }
  #qn-app .qn-note-title { max-width: 110px; }
  #qn-app .qn-note-preview { max-width: 120px; }
  #qn-app .qn-toolbar { gap: 4px; }
  #qn-app .qn-btn { padding: 5px 8px; font-size: 12px; }
}
</style>

<div class="qn-wrap">

  <!-- ツールバー -->
  <div class="qn-toolbar">
    <button class="qn-btn qn-btn-primary" onclick="QN.newNote()" title="新規メモ (Ctrl+N)">+ 新規</button>
    <button class="qn-btn" onclick="QN.downloadNote()" title="テキストファイルでダウンロード">&#8595; DL</button>
    <button class="qn-btn" onclick="QN.printNote()" title="印刷">&#128438; 印刷</button>
    <button class="qn-btn" onclick="QN.forceSave()" title="今すぐ保存 (Ctrl+S)">&#128190; 保存</button>
    <div class="qn-spacer"></div>
    <button class="qn-btn" onclick="QN.toggleTheme()" id="qn-theme-btn" title="ダーク/ライト切替">&#9790; ダーク</button>
  </div>

  <!-- 本体：サイドバー＋エディター -->
  <div class="qn-body">

    <!-- サイドバー -->
    <div class="qn-sidebar">
      <div class="qn-search-wrap">
        <input class="qn-search" id="qn-search" type="search" placeholder="メモを検索..." oninput="QN.onSearch(this.value)" />
      </div>
      <div class="qn-note-list" id="qn-note-list"></div>
      <div class="qn-sidebar-footer">
        <button class="qn-new-btn" onclick="QN.newNote()">+ 新規メモ</button>
      </div>
    </div>

    <!-- エディター -->
    <div class="qn-editor-pane" id="qn-editor-pane">
      <!-- 未選択時の空状態 -->
      <div class="qn-empty" id="qn-empty">
        <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/><polyline points="10 9 9 9 8 9"/></svg>
        <p>メモが選択されていません。<br><strong>+ 新規</strong>でメモを作成しましょう。</p>
      </div>
      <!-- タイトルバー -->
      <div id="qn-title-bar" class="qn-title-bar" style="display:none">
        <input class="qn-note-name-input" id="qn-note-name" type="text" placeholder="メモのタイトル..." oninput="QN.onTitleChange(this.value)" />
      </div>
      <!-- テキストエリア -->
      <textarea class="qn-textarea" id="qn-textarea" placeholder="ここにメモを書いてください..." style="display:none" oninput="QN.onTextChange(this.value)"></textarea>
      <!-- ステータスバー -->
      <div class="qn-status" id="qn-status" style="display:none">
        <span id="qn-words">0 文字</span>
        <span id="qn-chars">0 文字（スペース込）</span>
        <span class="qn-saved hidden" id="qn-saved-indicator">保存済 &#10003;</span>
      </div>
    </div>

  </div><!-- /.qn-body -->

</div><!-- /.qn-wrap -->

<script>
(function() {
  'use strict';

  /* ── Storage key ──────────────────────────────────────── */
  var STORE_KEY = 'qn_notes_v1_ja';
  var THEME_KEY = 'qn_theme_v1_ja';

  /* ── State ────────────────────────────────────────────── */
  var state = {
    notes: [],
    activeId: null,
    searchQuery: '',
    saveTimer: null,
    savedFlashTimer: null,
    dark: false
  };

  /* ── Helpers ──────────────────────────────────────────── */
  function uid() { return Date.now().toString(36) + Math.random().toString(36).slice(2, 7); }
  function esc(s) { return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;'); }

  function load() {
    try {
      var raw = localStorage.getItem(STORE_KEY);
      if (raw) state.notes = JSON.parse(raw);
    } catch(e) {}
    if (!Array.isArray(state.notes) || state.notes.length === 0) {
      state.notes = [{
        id: uid(),
        title: 'はじめのメモ',
        body: 'クイックメモ帳へようこそ！\n\nここに自由にメモを書いてください。2秒ごとにブラウザへ自動保存されます。\n\n使い方:\n- Ctrl+S で今すぐ保存\n- 「+ 新規」で複数のメモを管理\n- 検索欄でメモを横断検索\n- 「DL」ボタンで.txtファイルとして保存',
        updatedAt: Date.now()
      }];
      save();
    }
    try {
      state.dark = localStorage.getItem(THEME_KEY) === 'dark';
    } catch(e) {}
  }

  function save() {
    try { localStorage.setItem(STORE_KEY, JSON.stringify(state.notes)); } catch(e) {}
  }

  function getNote(id) { return state.notes.find(function(n){ return n.id === id; }); }

  function sortedNotes() {
    return state.notes.slice().sort(function(a,b){ return b.updatedAt - a.updatedAt; });
  }

  function filteredNotes() {
    var q = state.searchQuery.trim().toLowerCase();
    if (!q) return sortedNotes();
    return sortedNotes().filter(function(n) {
      return n.title.toLowerCase().indexOf(q) !== -1 || n.body.toLowerCase().indexOf(q) !== -1;
    });
  }

  /* ── Stats（日本語対応：文字数カウント）─────────────── */
  function updateStats(body) {
    /* 日本語は単語分割が難しいため、文字数（スペースなし）と全文字数を表示 */
    var noSpace = body.replace(/\s/g,'').length;
    var total = body.length;
    var wEl = document.getElementById('qn-words');
    var cEl = document.getElementById('qn-chars');
    if (wEl) wEl.textContent = noSpace + ' 文字（スペースなし）';
    if (cEl) cEl.textContent = total + ' 文字（全体）';
  }

  /* ── Render sidebar ───────────────────────────────────── */
  function renderList() {
    var list = document.getElementById('qn-note-list');
    if (!list) return;
    var notes = filteredNotes();
    var q = state.searchQuery.trim().toLowerCase();

    if (notes.length === 0) {
      list.innerHTML = '<div style="padding:12px;font-size:12px;color:var(--text-muted);text-align:center;">メモが見つかりません。</div>';
      return;
    }

    list.innerHTML = notes.map(function(n) {
      var active = n.id === state.activeId ? ' active' : '';
      var titleDisplay = q ? highlight(esc(n.title), q) : esc(n.title);
      var preview = n.body.replace(/\n/g, ' ').slice(0, 60);
      var previewDisplay = q ? highlight(esc(preview), q) : esc(preview);
      return '<div class="qn-note-item' + active + '" onclick="QN.selectNote(\'' + n.id + '\')" title="' + esc(n.title) + '">'
        + '<div class="qn-note-title">' + titleDisplay + '</div>'
        + '<div class="qn-note-preview">' + (previewDisplay || '<em>空のメモ</em>') + '</div>'
        + '<button class="qn-note-del" onclick="event.stopPropagation();QN.deleteNote(\'' + n.id + '\')" title="削除">&times;</button>'
        + '</div>';
    }).join('');
  }

  function highlight(str, q) {
    if (!q) return str;
    var re = new RegExp('(' + q.replace(/[.*+?^${}()|[\]\\]/g,'\\$&') + ')', 'gi');
    return str.replace(re, '<mark class="qn-highlight">$1</mark>');
  }

  /* ── Show/hide editor ─────────────────────────────────── */
  function showEditor(show) {
    var empty = document.getElementById('qn-empty');
    var titleBar = document.getElementById('qn-title-bar');
    var ta = document.getElementById('qn-textarea');
    var status = document.getElementById('qn-status');
    if (empty)    empty.style.display    = show ? 'none'  : 'flex';
    if (titleBar) titleBar.style.display = show ? 'flex'  : 'none';
    if (ta)       ta.style.display       = show ? 'block' : 'none';
    if (status)   status.style.display   = show ? 'flex'  : 'none';
  }

  /* ── Select note ──────────────────────────────────────── */
  function selectNote(id) {
    var note = getNote(id);
    if (!note) return;
    state.activeId = id;
    showEditor(true);
    var nameEl = document.getElementById('qn-note-name');
    var ta = document.getElementById('qn-textarea');
    if (nameEl) nameEl.value = note.title;
    if (ta) ta.value = note.body;
    updateStats(note.body);
    renderList();
  }

  /* ── Flash saved indicator ────────────────────────────── */
  function flashSaved() {
    var el = document.getElementById('qn-saved-indicator');
    if (!el) return;
    el.classList.remove('hidden');
    clearTimeout(state.savedFlashTimer);
    state.savedFlashTimer = setTimeout(function() { el.classList.add('hidden'); }, 2000);
  }

  /* ── Auto-save ────────────────────────────────────────── */
  function scheduleSave() {
    clearTimeout(state.saveTimer);
    state.saveTimer = setTimeout(function() { commitSave(); }, 2000);
  }

  function commitSave() {
    if (!state.activeId) return;
    save();
    flashSaved();
  }

  /* ── Theme ────────────────────────────────────────────── */
  function applyTheme() {
    var app = document.getElementById('qn-app');
    var btn = document.getElementById('qn-theme-btn');
    if (state.dark) {
      app.classList.add('qn-dark');
      if (btn) btn.textContent = '\u2600 ライト';
    } else {
      app.classList.remove('qn-dark');
      if (btn) btn.textContent = '\u263E ダーク';
    }
  }

  /* ── Public API ───────────────────────────────────────── */
  window.QN = {

    newNote: function() {
      var note = { id: uid(), title: '新規メモ', body: '', updatedAt: Date.now() };
      state.notes.unshift(note);
      save();
      selectNote(note.id);
      setTimeout(function() {
        var el = document.getElementById('qn-note-name');
        if (el) { el.focus(); el.select(); }
      }, 50);
    },

    deleteNote: function(id) {
      if (!window.confirm('このメモを削除しますか？元に戻せません。')) return;
      state.notes = state.notes.filter(function(n){ return n.id !== id; });
      save();
      if (state.activeId === id) {
        state.activeId = null;
        showEditor(false);
        var remaining = sortedNotes();
        if (remaining.length > 0) selectNote(remaining[0].id);
      }
      renderList();
    },

    selectNote: function(id) { selectNote(id); },

    onTitleChange: function(val) {
      if (!state.activeId) return;
      var note = getNote(state.activeId);
      if (!note) return;
      note.title = val || '無題';
      note.updatedAt = Date.now();
      renderList();
      scheduleSave();
    },

    onTextChange: function(val) {
      if (!state.activeId) return;
      var note = getNote(state.activeId);
      if (!note) return;
      note.body = val;
      note.updatedAt = Date.now();
      updateStats(val);
      renderList();
      scheduleSave();
    },

    onSearch: function(val) {
      state.searchQuery = val;
      renderList();
    },

    forceSave: function() {
      clearTimeout(state.saveTimer);
      commitSave();
    },

    downloadNote: function() {
      if (!state.activeId) { alert('メモを選択してください。'); return; }
      var note = getNote(state.activeId);
      if (!note) return;
      var content = note.title + '\n' + new Array(note.title.length + 1).join('=') + '\n\n' + note.body;
      var blob = new Blob([content], { type: 'text/plain;charset=utf-8' });
      var url = URL.createObjectURL(blob);
      var a = document.createElement('a');
      a.href = url;
      a.download = (note.title.replace(/[^\w\u3000-\u9fff\u30a0-\u30ff\u3041-\u3096]/g,'_') || 'memo') + '.txt';
      document.body.appendChild(a); a.click();
      setTimeout(function() { document.body.removeChild(a); URL.revokeObjectURL(url); }, 100);
    },

    printNote: function() {
      if (!state.activeId) { alert('メモを選択してください。'); return; }
      var note = getNote(state.activeId);
      if (!note) return;
      var w = window.open('', '_blank');
      w.document.write('<!DOCTYPE html><html><head><title>' + esc(note.title) + '</title>'
        + '<meta charset="UTF-8">'
        + '<style>body{font-family:"Hiragino Kaku Gothic ProN","Hiragino Sans",Meiryo,sans-serif;max-width:700px;margin:40px auto;font-size:15px;line-height:1.9;}'
        + 'h1{font-size:20px;margin-bottom:8px;}pre{white-space:pre-wrap;word-break:break-word;}</style></head>'
        + '<body><h1>' + esc(note.title) + '</h1><pre>' + esc(note.body) + '</pre></body></html>');
      w.document.close();
      w.focus();
      w.print();
    },

    toggleTheme: function() {
      state.dark = !state.dark;
      try { localStorage.setItem(THEME_KEY, state.dark ? 'dark' : 'light'); } catch(e) {}
      applyTheme();
    }
  };

  /* ── Keyboard shortcuts ───────────────────────────────── */
  document.addEventListener('keydown', function(e) {
    var tag = (e.target && e.target.tagName) ? e.target.tagName.toUpperCase() : '';
    if ((e.ctrlKey || e.metaKey) && e.key === 's') {
      e.preventDefault();
      QN.forceSave();
    }
    if ((e.ctrlKey || e.metaKey) && e.key === 'n' && tag !== 'INPUT' && tag !== 'TEXTAREA') {
      e.preventDefault();
      QN.newNote();
    }
  });

  /* ── Init ─────────────────────────────────────────────── */
  load();
  applyTheme();
  renderList();
  var first = sortedNotes()[0];
  if (first) selectNote(first.id);

})();
</script>

</div><!-- /#qn-app -->

<!-- freee CTA -->
<div id="qn-freee-cta">
  <strong>メモ・タスク管理を整えたら、経理もクラウドでスッキリさせませんか？</strong><br>
  フリーランス・個人事業主の方へ。freeeなら確定申告・帳簿記帳・請求書発行がすべてひとつで完結。領収書スキャンから申告書提出まで自動化できます。<br>
  <a class="qn-freee-link" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow" target="_blank">freeeを無料で試す &#8594;</a>
</div>

<!-- 関連ツール -->
<div id="qn-related">
  <strong>関連ツール：</strong>
  <a href="/ja/tools/markdown-editor/">Markdownエディター</a> &nbsp;&middot;&nbsp;
  <a href="/ja/tools/word-counter/">文字数カウンター</a> &nbsp;&middot;&nbsp;
  <a href="/ja/tools/text-case-converter/">テキストケース変換</a>
</div>

---

## クイックメモ帳の使い方

右側の大きなテキストエリアに自由に書いてください。入力した内容は **2秒ごとにブラウザのlocalStorageへ自動保存** されます。アカウント作成不要・サーバー送信なし・インターネット接続なしでも動作します。ステータスバーの「保存済 ✓」が表示されるたびに保存が完了しています。**Ctrl+S**（MacはCmd+S）で即時保存も可能です。

**複数のメモ：** ツールバーまたはサイドバーの「+ 新規」をクリックすると新しいメモを作成できます。メモは最終更新日時の新しい順にサイドバーへ一覧表示されます。クリックするだけで瞬時に切り替えられます。

**タイトル変更：** エディター上部のタイトル欄をクリックして直接編集できます。入力と同時にサイドバーの一覧にも反映されます。

**検索：** サイドバー上部の検索欄に入力すると、全メモのタイトルと本文を横断検索します。一致したテキストは黄色でハイライト表示されます。

**ダウンロード：** 「DL」ボタンで現在のメモを `.txt` ファイルとして端末に保存できます。ファイル名はメモのタイトルから自動生成されます。

**削除：** サイドバーのメモ項目にマウスを乗せると × ボタンが表示されます。クリック後に確認ダイアログが表示されるので、誤操作による削除を防げます。

**テーマ切替：** ツールバー右端のボタンでライト／ダークモードを切り替えられます。設定はブラウザに記憶されるため、次回アクセス時にも反映されます。

**印刷：** 「印刷」ボタンをクリックすると、印刷に最適化されたプレビューウィンドウが開きます。

## なぜブラウザメモ帳が便利なのか

ブラウザ上で動作するメモ帳の最大のメリットは、インストール不要でどのデバイスからでもアクセスできる点です。会社のPC・自宅のMac・スマートフォンと、ブラウザさえあれば同じツールを使えます。データはすべて端末のlocalStorageに保存され、外部サーバーへは一切送信されません。

クラウド型のメモサービスと異なり、インターネット接続が途切れても書き続けられます。会議中のメモ取り、アイデアの走り書き、一時的なテキスト置き場など、気軽に使えるのが強みです。

なお、localStorageのデータは同じブラウザ・端末でのみ共有されます。複数デバイス間での同期は行いません。また、ブラウザのデータ消去（キャッシュ・サイトデータの削除）を行うとメモも消えます。大切なメモは定期的に「DL」ボタンでバックアップを取ることをおすすめします。

## 関連ツール

> Markdownで文書を書く → [Markdownエディター](/ja/tools/markdown-editor/)

> 文字数・単語数をカウント → [文字数カウンター](/ja/tools/word-counter/)

> テキストの大文字・小文字を変換 → [テキストケース変換](/ja/tools/text-case-converter/)

<small>※ freeeへのリンクはアフィリエイト広告を含みます。</small>
