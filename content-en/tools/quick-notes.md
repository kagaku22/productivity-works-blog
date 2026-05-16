---
title: "Quick Notes - Online Notepad"
date: 2025-05-16
description: "Free online notepad. Write notes instantly with auto-save to browser. Supports multiple notes, search, and download. No sign-up required. Works offline."
categories: ["Free Tools"]
tags: ["online notepad", "quick notes", "note taking", "auto-save", "offline notepad", "browser notepad", "productivity tool"]
slug: "quick-notes"
cover:
  image: "/images/covers/quick-notes.png"
  alt: "Quick Notes - Free Online Notepad"
ShowToc: false
---

<div id="qn-app">

<style>
/* ── Reset & Root ─────────────────────────────────────── */
#qn-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", sans-serif;
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
  line-height: 1.75;
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

  <!-- Toolbar -->
  <div class="qn-toolbar">
    <button class="qn-btn qn-btn-primary" onclick="QN.newNote()" title="New note (Ctrl+N)">+ New</button>
    <button class="qn-btn" onclick="QN.downloadNote()" title="Download current note as .txt">&#8595; Download</button>
    <button class="qn-btn" onclick="QN.printNote()" title="Print current note">&#128438; Print</button>
    <button class="qn-btn" onclick="QN.forceSave()" title="Force save (Ctrl+S)">&#128190; Save</button>
    <div class="qn-spacer"></div>
    <button class="qn-btn" onclick="QN.toggleTheme()" id="qn-theme-btn" title="Toggle dark/light theme">&#9790; Dark</button>
  </div>

  <!-- Body: sidebar + editor -->
  <div class="qn-body">

    <!-- Sidebar -->
    <div class="qn-sidebar">
      <div class="qn-search-wrap">
        <input class="qn-search" id="qn-search" type="search" placeholder="Search notes..." oninput="QN.onSearch(this.value)" />
      </div>
      <div class="qn-note-list" id="qn-note-list"></div>
      <div class="qn-sidebar-footer">
        <button class="qn-new-btn" onclick="QN.newNote()">+ New Note</button>
      </div>
    </div>

    <!-- Editor -->
    <div class="qn-editor-pane" id="qn-editor-pane">
      <!-- empty state shown when no note selected -->
      <div class="qn-empty" id="qn-empty">
        <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/><polyline points="10 9 9 9 8 9"/></svg>
        <p>No note selected.<br>Create one with <strong>+ New</strong>.</p>
      </div>
      <!-- title bar -->
      <div id="qn-title-bar" class="qn-title-bar" style="display:none">
        <input class="qn-note-name-input" id="qn-note-name" type="text" placeholder="Note title..." oninput="QN.onTitleChange(this.value)" />
      </div>
      <!-- textarea -->
      <textarea class="qn-textarea" id="qn-textarea" placeholder="Start writing your note here..." style="display:none" oninput="QN.onTextChange(this.value)"></textarea>
      <!-- status bar -->
      <div class="qn-status" id="qn-status" style="display:none">
        <span id="qn-words">0 words</span>
        <span id="qn-chars">0 chars</span>
        <span class="qn-saved hidden" id="qn-saved-indicator">Saved &#10003;</span>
      </div>
    </div>

  </div><!-- /.qn-body -->

</div><!-- /.qn-wrap -->

<script>
(function() {
  'use strict';

  /* ── Storage key ──────────────────────────────────────── */
  var STORE_KEY = 'qn_notes_v1';
  var THEME_KEY = 'qn_theme_v1';

  /* ── State ────────────────────────────────────────────── */
  var state = {
    notes: [],       // [{id, title, body, updatedAt}]
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
        title: 'Welcome Note',
        body: 'Welcome to Quick Notes!\n\nStart typing here. Your notes are auto-saved every 2 seconds to your browser.\n\nTips:\n- Press Ctrl+S to force save\n- Create multiple notes with "+ New"\n- Search across all notes using the search bar\n- Download any note as a .txt file',
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

  /* ── Stats ────────────────────────────────────────────── */
  function updateStats(body) {
    var words = body.trim() === '' ? 0 : body.trim().split(/\s+/).length;
    var chars = body.length;
    var wEl = document.getElementById('qn-words');
    var cEl = document.getElementById('qn-chars');
    if (wEl) wEl.textContent = words + (words === 1 ? ' word' : ' words');
    if (cEl) cEl.textContent = chars + (chars === 1 ? ' char' : ' chars');
  }

  /* ── Render sidebar ───────────────────────────────────── */
  function renderList() {
    var list = document.getElementById('qn-note-list');
    if (!list) return;
    var notes = filteredNotes();
    var q = state.searchQuery.trim().toLowerCase();

    if (notes.length === 0) {
      list.innerHTML = '<div style="padding:12px;font-size:12px;color:var(--text-muted);text-align:center;">No notes found.</div>';
      return;
    }

    list.innerHTML = notes.map(function(n) {
      var active = n.id === state.activeId ? ' active' : '';
      var titleDisplay = q ? highlight(esc(n.title), q) : esc(n.title);
      var preview = n.body.replace(/\n/g, ' ').slice(0, 60);
      var previewDisplay = q ? highlight(esc(preview), q) : esc(preview);
      return '<div class="qn-note-item' + active + '" onclick="QN.selectNote(\'' + n.id + '\')" title="' + esc(n.title) + '">'
        + '<div class="qn-note-title">' + titleDisplay + '</div>'
        + '<div class="qn-note-preview">' + (previewDisplay || '<em>Empty</em>') + '</div>'
        + '<button class="qn-note-del" onclick="event.stopPropagation();QN.deleteNote(\'' + n.id + '\')" title="Delete note">&times;</button>'
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
    if (empty)   empty.style.display   = show ? 'none' : 'flex';
    if (titleBar) titleBar.style.display = show ? 'flex' : 'none';
    if (ta)      ta.style.display      = show ? 'block' : 'none';
    if (status)  status.style.display  = show ? 'flex'  : 'none';
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
      if (btn) btn.textContent = '\u2600 Light';
    } else {
      app.classList.remove('qn-dark');
      if (btn) btn.textContent = '\u263E Dark';
    }
  }

  /* ── Public API ───────────────────────────────────────── */
  window.QN = {

    newNote: function() {
      var note = { id: uid(), title: 'New Note', body: '', updatedAt: Date.now() };
      state.notes.unshift(note);
      save();
      selectNote(note.id);
      // Focus title so user can rename immediately
      setTimeout(function() {
        var el = document.getElementById('qn-note-name');
        if (el) { el.focus(); el.select(); }
      }, 50);
    },

    deleteNote: function(id) {
      if (!window.confirm('Delete this note? This cannot be undone.')) return;
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
      note.title = val || 'Untitled';
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
      if (!state.activeId) { alert('Select a note first.'); return; }
      var note = getNote(state.activeId);
      if (!note) return;
      var content = note.title + '\n' + new Array(note.title.length + 1).join('=') + '\n\n' + note.body;
      var blob = new Blob([content], { type: 'text/plain;charset=utf-8' });
      var url = URL.createObjectURL(blob);
      var a = document.createElement('a');
      a.href = url;
      a.download = (note.title.replace(/[^a-z0-9_\-]/gi,'_') || 'note') + '.txt';
      document.body.appendChild(a); a.click();
      setTimeout(function() { document.body.removeChild(a); URL.revokeObjectURL(url); }, 100);
    },

    printNote: function() {
      if (!state.activeId) { alert('Select a note first.'); return; }
      var note = getNote(state.activeId);
      if (!note) return;
      var w = window.open('', '_blank');
      w.document.write('<!DOCTYPE html><html><head><title>' + esc(note.title) + '</title>'
        + '<style>body{font-family:serif;max-width:700px;margin:40px auto;font-size:15px;line-height:1.8;}'
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

---

## How to Use Quick Notes

Type in the large text area on the right. Your note is saved automatically to your browser every 2 seconds — no account, no server, no internet connection needed after the page loads. The last-saved indicator in the status bar confirms each save. Press **Ctrl+S** (or Cmd+S on Mac) at any time to force an immediate save.

**Multiple notes:** Click **+ New** in the toolbar or sidebar to create a new note. Each note gets its own entry in the left sidebar, sorted by most recently edited. Click any note in the list to switch to it instantly.

**Renaming:** Click the title bar at the top of the editor to rename the current note. The title updates in the sidebar as you type.

**Search:** Type in the search box above the note list to filter notes by title or content. Matching text is highlighted in yellow.

**Download:** The Download button exports the current note as a plain `.txt` file to your device. The filename is based on the note title.

**Delete:** Hover over any note in the sidebar to reveal the × button, then click to delete. A confirmation prompt prevents accidental deletion.

**Theme:** Toggle between light and dark mode with the button in the top-right corner of the toolbar. Your preference is remembered across visits.

**Print:** Click the Print button to open a clean print-preview window formatted for paper.

## Why Keep Notes in Your Browser?

Browser-based notepads have one major advantage over native apps: they are available on any device with a browser, with zero installation. When you are on a work computer, a public library terminal, or a friend's laptop, Quick Notes is just a bookmark away. All data lives in your browser's `localStorage`, which means it stays private — nothing is ever uploaded.

For sensitive information, however, keep in mind that `localStorage` is accessible to JavaScript running on the same origin, so treat it like any local file on your computer: fine for working notes, but use proper encryption tools for truly sensitive material.

Unlike cloud note-taking services, Quick Notes works entirely offline after the first page load. If your internet drops mid-session, you will not lose anything — the auto-save timer keeps running and your data stays local.

## Related Tools

> Format and preview Markdown → [Markdown Editor](/tools/markdown-editor/)

> Count words and characters in your writing → [Word Counter](/tools/word-counter/)

> Change text case instantly → [Text Case Converter](/tools/text-case-converter/)
