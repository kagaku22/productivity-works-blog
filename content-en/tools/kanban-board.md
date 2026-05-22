---
title: "Kanban Board"
date: 2025-05-16
description: "Free online Kanban board. Organize tasks in To Do, In Progress, and Done columns with drag-and-drop — data saved locally, no sign-up required."
categories: ["Free Tools"]
tags: ["Productivity", "Business", "Free Tools"]
slug: "kanban-board"
ShowToc: false
cover:
  image: "/images/covers/kanban-board.png"
  alt: "Kanban Board"
---

<div id="kb-app">

<style>
/* ── Reset & base ── */
#kb-app *, #kb-app *::before, #kb-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}
#kb-app {
--bg:        #0f172a;
--surface:   #1e293b;
--surface2:  #334155;
--border:    #475569;
--text:      #f1f5f9;
--text-muted:#94a3b8;
--accent:    #38bdf8;
--danger:    #f87171;
--radius:    8px;
--col-w:     300px;
--shadow:    0 4px 16px rgba(0,0,0,.45);

--lbl-red:   #ef4444;
--lbl-orange:#f97316;
--lbl-green: #22c55e;
--lbl-blue:  #3b82f6;
--lbl-none:  #475569;

font-family: system-ui, -apple-system, "Segoe UI", sans-serif;
font-size: 15px;
color: var(--text);
background: var(--bg);
padding: 20px 16px 40px;
min-height: 60vh;
}

/* ── Toolbar ── */
#kb-app .kb-toolbar {
display: flex;
flex-wrap: wrap;
gap: 8px;
align-items: center;
margin-bottom: 20px;
}
#kb-app .kb-toolbar h2 {
font-size: 1.25rem;
font-weight: 700;
letter-spacing: .02em;
margin-right: auto;
}
#kb-app button {
cursor: pointer;
border: none;
border-radius: var(--radius);
font-size: 13px;
font-weight: 600;
padding: 7px 14px;
transition: opacity .15s, background .15s;
}
#kb-app button:hover { opacity: .85; }
#kb-app .btn-primary  { background: var(--accent); color: #0f172a; }
#kb-app .btn-ghost    { background: var(--surface2); color: var(--text); }
#kb-app .btn-danger   { background: var(--danger);  color: #fff; }
#kb-app .btn-icon     { background: transparent; color: var(--text-muted); padding: 4px 8px; font-size: 16px; }
#kb-app .btn-icon:hover { color: var(--text); }

/* ── Board ── */
#kb-app .kb-board {
display: flex;
gap: 16px;
overflow-x: auto;
align-items: flex-start;
padding-bottom: 12px;
}
#kb-app .kb-board::-webkit-scrollbar { height: 6px; }
#kb-app .kb-board::-webkit-scrollbar-track { background: transparent; }
#kb-app .kb-board::-webkit-scrollbar-thumb { background: var(--border); border-radius: 99px; }

/* ── Column ── */
#kb-app .kb-col {
background: var(--surface);
border: 1px solid var(--border);
border-radius: 10px;
width: var(--col-w);
min-width: var(--col-w);
display: flex;
flex-direction: column;
max-height: 80vh;
transition: box-shadow .15s;
}
#kb-app .kb-col.drag-over {
box-shadow: 0 0 0 2px var(--accent);
}
#kb-app .kb-col-header {
display: flex;
align-items: center;
gap: 6px;
padding: 12px 12px 10px;
border-bottom: 1px solid var(--border);
flex-shrink: 0;
}
#kb-app .kb-col-title {
flex: 1;
font-weight: 700;
font-size: .95rem;
background: transparent;
border: 1px solid transparent;
border-radius: 4px;
color: var(--text);
padding: 2px 4px;
cursor: text;
}
#kb-app .kb-col-title:focus {
outline: none;
border-color: var(--accent);
background: var(--surface2);
}
#kb-app .kb-col-count {
background: var(--surface2);
color: var(--text-muted);
border-radius: 99px;
font-size: 11px;
font-weight: 700;
padding: 1px 8px;
min-width: 24px;
text-align: center;
}

#kb-app .kb-cards {
flex: 1;
overflow-y: auto;
padding: 10px 10px 6px;
display: flex;
flex-direction: column;
gap: 8px;
min-height: 60px;
}
#kb-app .kb-cards::-webkit-scrollbar { width: 4px; }
#kb-app .kb-cards::-webkit-scrollbar-thumb { background: var(--border); border-radius: 99px; }

#kb-app .kb-col-footer {
padding: 8px 10px 12px;
flex-shrink: 0;
}
#kb-app .btn-add-card {
width: 100%;
background: var(--surface2);
color: var(--text-muted);
border-radius: var(--radius);
padding: 7px 10px;
font-size: 13px;
text-align: left;
}
#kb-app .btn-add-card:hover { color: var(--text); }

/* ── Card ── */
#kb-app .kb-card {
background: var(--surface2);
border: 1px solid var(--border);
border-left: 4px solid var(--lbl-none);
border-radius: var(--radius);
padding: 10px 10px 8px;
cursor: grab;
user-select: none;
position: relative;
transition: box-shadow .15s, transform .1s;
}
#kb-app .kb-card:active { cursor: grabbing; }
#kb-app .kb-card.dragging {
opacity: .4;
transform: scale(.97);
}
#kb-app .kb-card[data-label="red"]    { border-left-color: var(--lbl-red); }
#kb-app .kb-card[data-label="orange"] { border-left-color: var(--lbl-orange); }
#kb-app .kb-card[data-label="green"]  { border-left-color: var(--lbl-green); }
#kb-app .kb-card[data-label="blue"]   { border-left-color: var(--lbl-blue); }

#kb-app .kb-card-title {
font-weight: 600;
font-size: .9rem;
margin-bottom: 4px;
word-break: break-word;
}
#kb-app .kb-card-desc {
font-size: .8rem;
color: var(--text-muted);
word-break: break-word;
white-space: pre-wrap;
}
#kb-app .kb-card-actions {
display: flex;
gap: 4px;
justify-content: flex-end;
margin-top: 8px;
}

/* ── Add-column button ── */
#kb-app .kb-add-col {
background: var(--surface);
border: 2px dashed var(--border);
border-radius: 10px;
width: 220px;
min-width: 220px;
height: 56px;
display: flex;
align-items: center;
justify-content: center;
color: var(--text-muted);
font-size: 13px;
font-weight: 600;
cursor: pointer;
flex-shrink: 0;
transition: border-color .15s, color .15s;
}
#kb-app .kb-add-col:hover { border-color: var(--accent); color: var(--text); }

/* ── Modal overlay ── */
#kb-app .kb-overlay {
position: fixed;
inset: 0;
background: rgba(0,0,0,.65);
display: flex;
align-items: center;
justify-content: center;
z-index: 9999;
padding: 16px;
}
#kb-app .kb-overlay.hidden { display: none; }
#kb-app .kb-modal {
background: var(--surface);
border: 1px solid var(--border);
border-radius: 12px;
width: 100%;
max-width: 440px;
padding: 24px;
box-shadow: var(--shadow);
display: flex;
flex-direction: column;
gap: 14px;
}
#kb-app .kb-modal h3 {
font-size: 1.05rem;
font-weight: 700;
}
#kb-app .kb-modal label {
display: block;
font-size: 12px;
color: var(--text-muted);
margin-bottom: 4px;
font-weight: 600;
text-transform: uppercase;
letter-spacing: .05em;
}
#kb-app .kb-modal input[type="text"],
#kb-app .kb-modal textarea,
#kb-app .kb-modal select {
width: 100%;
background: var(--surface2);
border: 1px solid var(--border);
border-radius: var(--radius);
color: var(--text);
font-size: 14px;
padding: 8px 10px;
font-family: inherit;
resize: vertical;
}
#kb-app .kb-modal input[type="text"]:focus,
#kb-app .kb-modal textarea:focus,
#kb-app .kb-modal select:focus {
outline: none;
border-color: var(--accent);
}
#kb-app .kb-modal textarea { min-height: 80px; }
#kb-app .kb-modal .kb-modal-actions {
display: flex;
gap: 8px;
justify-content: flex-end;
flex-wrap: wrap;
}

/* ── Label dots ── */
#kb-app .kb-label-row {
display: flex;
gap: 8px;
align-items: center;
}
#kb-app .kb-label-dot {
width: 22px;
height: 22px;
border-radius: 50%;
cursor: pointer;
border: 2px solid transparent;
transition: border-color .1s, transform .1s;
}
#kb-app .kb-label-dot:hover { transform: scale(1.15); }
#kb-app .kb-label-dot.selected { border-color: #fff; transform: scale(1.2); }
#kb-app .kb-label-dot[data-v="none"]   { background: var(--lbl-none); }
#kb-app .kb-label-dot[data-v="red"]    { background: var(--lbl-red); }
#kb-app .kb-label-dot[data-v="orange"] { background: var(--lbl-orange); }
#kb-app .kb-label-dot[data-v="green"]  { background: var(--lbl-green); }
#kb-app .kb-label-dot[data-v="blue"]   { background: var(--lbl-blue); }

/* ── Move dropdown (mobile fallback) ── */
#kb-app .kb-card select.move-select {
background: var(--surface);
border: 1px solid var(--border);
color: var(--text);
border-radius: 4px;
font-size: 12px;
padding: 2px 6px;
cursor: pointer;
max-width: 110px;
}

/* ── Toast ── */
#kb-app .kb-toast {
position: fixed;
bottom: 24px;
left: 50%;
transform: translateX(-50%) translateY(80px);
background: var(--surface2);
color: var(--text);
border: 1px solid var(--border);
border-radius: var(--radius);
padding: 10px 20px;
font-size: 13px;
z-index: 10000;
transition: transform .3s ease;
white-space: nowrap;
pointer-events: none;
}
#kb-app .kb-toast.show { transform: translateX(-50%) translateY(0); }

/* ── Responsive ── */
@media (max-width: 600px) {
#kb-app .kb-col { min-width: 85vw; width: 85vw; }
#kb-app .kb-add-col { min-width: 70vw; width: 70vw; }
}
</style>

<!-- Toolbar -->
<div class="kb-toolbar">
<h2>Kanban Board</h2>
<button class="btn-ghost" id="kb-btn-import">Import JSON</button>
<button class="btn-ghost" id="kb-btn-export">Export JSON</button>
<button class="btn-danger" id="kb-btn-clear">Clear Board</button>
</div>

<!-- Board container -->
<div class="kb-board" id="kb-board"></div>

<!-- Card modal -->
<div class="kb-overlay hidden" id="kb-modal-overlay">
<div class="kb-modal" role="dialog" aria-modal="true" aria-labelledby="kb-modal-title">
<h3 id="kb-modal-title">Add Card</h3>
<div>
<label for="kb-input-title">Title</label>
<input type="text" id="kb-input-title" placeholder="Card title…" maxlength="120">
</div>
<div>
<label for="kb-input-desc">Description (optional)</label>
<textarea id="kb-input-desc" placeholder="Details, notes…" maxlength="600"></textarea>
</div>
<div>
<label>Priority label</label>
<div class="kb-label-row" id="kb-label-row">
<span class="kb-label-dot selected" data-v="none"  title="None"></span>
<span class="kb-label-dot"          data-v="red"   title="High"></span>
<span class="kb-label-dot"          data-v="orange"title="Medium"></span>
<span class="kb-label-dot"          data-v="green" title="Low"></span>
<span class="kb-label-dot"          data-v="blue"  title="Info"></span>
</div>
</div>
<div class="kb-modal-actions">
<button class="btn-ghost"   id="kb-modal-cancel">Cancel</button>
<button class="btn-danger hidden" id="kb-modal-delete">Delete Card</button>
<button class="btn-primary" id="kb-modal-save">Save</button>
</div>
</div>
</div>

<!-- Import file input (hidden) -->
<input type="file" id="kb-file-input" accept=".json" style="display:none">

<!-- Toast -->
<div class="kb-toast" id="kb-toast"></div>

<script>
(function () {
'use strict';

/* ── State ── */
const STORAGE_KEY = 'kb_board_v1';
let state = { columns: [], cards: [] };
let dragCardId = null;

/* modal edit state */
let modalMode  = 'add';   // 'add' | 'edit'
let modalColId = null;
let modalCardId= null;
let selectedLabel = 'none';

/* ── Utilities ── */
const uid = () => Math.random().toString(36).slice(2, 10) + Date.now().toString(36);

function save() {
try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); } catch(_) {}
}

function load() {
try {
const raw = localStorage.getItem(STORAGE_KEY);
if (raw) { const parsed = JSON.parse(raw); if (parsed && parsed.columns) state = parsed; }
} catch(_) {}
}

function showToast(msg) {
const t = document.getElementById('kb-toast');
t.textContent = msg;
t.classList.add('show');
setTimeout(() => t.classList.remove('show'), 2200);
}

/* ── Default data ── */
function initDefault() {
const colIds = [uid(), uid(), uid()];
state = {
columns: [
{ id: colIds[0], title: 'To Do' },
{ id: colIds[1], title: 'In Progress' },
{ id: colIds[2], title: 'Done' },
],
cards: [
{ id: uid(), colId: colIds[0], title: 'Welcome to your Kanban Board', desc: 'Drag cards between columns, click to edit.', label: 'blue' },
{ id: uid(), colId: colIds[0], title: 'Add a new card', desc: '', label: 'none' },
{ id: uid(), colId: colIds[1], title: 'Review project scope', desc: '', label: 'orange' },
{ id: uid(), colId: colIds[2], title: 'Set up board', desc: '', label: 'green' },
]
};
save();
}

/* ── Render ── */
function cardsForCol(colId) {
return state.cards.filter(c => c.colId === colId);
}

function isMobile() {
return window.matchMedia('(max-width: 700px)').matches;
}

function renderBoard() {
const board = document.getElementById('kb-board');
board.innerHTML = '';

state.columns.forEach(col => {
const cards = cardsForCol(col.id);

const colEl = document.createElement('div');
colEl.className = 'kb-col';
colEl.dataset.colId = col.id;

/* ── header ── */
colEl.innerHTML = `
<div class="kb-col-header">
<input class="kb-col-title" value="${escHtml(col.title)}" aria-label="Column title" maxlength="50">
<span class="kb-col-count">${cards.length}</span>
<button class="btn-icon kb-del-col" title="Delete column" aria-label="Delete column">&#x2715;</button>
</div>
<div class="kb-cards" data-col-id="${col.id}"></div>
<div class="kb-col-footer">
<button class="btn-add-card" data-col-id="${col.id}">&#xFF0B; Add card</button>
</div>`;

board.appendChild(colEl);

/* column title inline edit */
const titleInput = colEl.querySelector('.kb-col-title');
titleInput.addEventListener('change', () => {
col.title = titleInput.value.trim() || col.title;
titleInput.value = col.title;
save();
refreshCounts();
refreshMoveDropdowns();
});

/* delete column */
colEl.querySelector('.kb-del-col').addEventListener('click', () => {
if (!confirm(`Delete column "${col.title}" and all its cards?`)) return;
state.cards   = state.cards.filter(c => c.colId !== col.id);
state.columns = state.columns.filter(c => c.id !== col.id);
save();
renderBoard();
});

/* add card button */
colEl.querySelector('.btn-add-card').addEventListener('click', () => openModal('add', col.id));

/* ── cards area ── */
const cardsArea = colEl.querySelector('.kb-cards');
setupDropZone(cardsArea, col.id);

cards.forEach(card => {
const cardEl = createCardEl(card);
cardsArea.appendChild(cardEl);
});
});

/* ── Add column button ── */
const addColBtn = document.createElement('button');
addColBtn.className = 'kb-add-col';
addColBtn.textContent = '+ Add Column';
addColBtn.addEventListener('click', () => {
const title = prompt('Column name:');
if (!title || !title.trim()) return;
state.columns.push({ id: uid(), title: title.trim() });
save();
renderBoard();
});
board.appendChild(addColBtn);
}

function createCardEl(card) {
const el = document.createElement('div');
el.className = 'kb-card';
el.draggable = true;
el.dataset.cardId = card.id;
el.dataset.label  = card.label || 'none';

const moveOptions = state.columns
.filter(c => c.id !== card.colId)
.map(c => `<option value="${c.id}">${escHtml(c.title)}</option>`)
.join('');

el.innerHTML = `
<div class="kb-card-title">${escHtml(card.title)}</div>
${card.desc ? `<div class="kb-card-desc">${escHtml(card.desc)}</div>` : ''}
<div class="kb-card-actions">
${moveOptions ? `<select class="move-select" title="Move to column" aria-label="Move card to column">
<option value="">Move to…</option>${moveOptions}
</select>` : ''}
<button class="btn-icon kb-edit-card" title="Edit" aria-label="Edit card">&#x270E;</button>
</div>`;

/* drag */
el.addEventListener('dragstart', e => {
dragCardId = card.id;
el.classList.add('dragging');
e.dataTransfer.effectAllowed = 'move';
});
el.addEventListener('dragend', () => {
dragCardId = null;
el.classList.remove('dragging');
document.querySelectorAll('#kb-board .kb-col').forEach(c => c.classList.remove('drag-over'));
});

/* touch support */
setupTouch(el, card.id);

/* edit button */
el.querySelector('.kb-edit-card').addEventListener('click', e => {
e.stopPropagation();
openModal('edit', card.colId, card.id);
});

/* move dropdown */
const sel = el.querySelector('.move-select');
if (sel) {
sel.addEventListener('change', () => {
const targetColId = sel.value;
if (!targetColId) return;
const c = state.cards.find(x => x.id === card.id);
if (c) { c.colId = targetColId; save(); renderBoard(); }
});
}

return el;
}

/* ── Drop zones ── */
function setupDropZone(area, colId) {
area.addEventListener('dragover', e => {
e.preventDefault();
e.dataTransfer.dropEffect = 'move';
area.closest('.kb-col').classList.add('drag-over');
});
area.addEventListener('dragleave', e => {
if (!area.contains(e.relatedTarget)) {
area.closest('.kb-col').classList.remove('drag-over');
}
});
area.addEventListener('drop', e => {
e.preventDefault();
area.closest('.kb-col').classList.remove('drag-over');
if (!dragCardId) return;
const card = state.cards.find(c => c.id === dragCardId);
if (card && card.colId !== colId) {
card.colId = colId;
save();
renderBoard();
}
});
}

/* ── Touch drag (simple touch-to-move via move dropdown, plus basic touch scroll) ── */
function setupTouch(el, cardId) {
let startX, startY, ghost = null, moved = false;
el.addEventListener('touchstart', e => {
const t = e.touches[0];
startX = t.clientX; startY = t.clientY;
moved = false;
}, { passive: true });

el.addEventListener('touchmove', e => {
const t = e.touches[0];
const dx = t.clientX - startX, dy = t.clientY - startY;
if (Math.abs(dx) > 8 || Math.abs(dy) > 8) moved = true;
}, { passive: true });
}

/* ── Counts & dropdown refresh (without full re-render) ── */
function refreshCounts() {
state.columns.forEach(col => {
const colEl = document.querySelector(`.kb-col[data-col-id="${col.id}"]`);
if (!colEl) return;
const cnt = colEl.querySelector('.kb-col-count');
if (cnt) cnt.textContent = cardsForCol(col.id).length;
});
}

function refreshMoveDropdowns() {
/* cheapest: just re-render */
renderBoard();
}

/* ── Modal ── */
function openModal(mode, colId, cardId) {
modalMode   = mode;
modalColId  = colId;
modalCardId = cardId || null;
selectedLabel = 'none';

const overlay = document.getElementById('kb-modal-overlay');
const titleEl = document.getElementById('kb-modal-title');
const inputTitle = document.getElementById('kb-input-title');
const inputDesc  = document.getElementById('kb-input-desc');
const deleteBtn  = document.getElementById('kb-modal-delete');

if (mode === 'edit') {
const card = state.cards.find(c => c.id === cardId);
titleEl.textContent  = 'Edit Card';
inputTitle.value     = card.title;
inputDesc.value      = card.desc || '';
selectedLabel        = card.label || 'none';
deleteBtn.classList.remove('hidden');
} else {
titleEl.textContent  = 'Add Card';
inputTitle.value     = '';
inputDesc.value      = '';
selectedLabel        = 'none';
deleteBtn.classList.add('hidden');
}

/* sync label dots */
document.querySelectorAll('#kb-label-row .kb-label-dot').forEach(dot => {
dot.classList.toggle('selected', dot.dataset.v === selectedLabel);
});

overlay.classList.remove('hidden');
inputTitle.focus();
}

function closeModal() {
document.getElementById('kb-modal-overlay').classList.add('hidden');
}

/* ── Modal events ── */
document.getElementById('kb-modal-cancel').addEventListener('click', closeModal);
document.getElementById('kb-modal-overlay').addEventListener('click', e => {
if (e.target === document.getElementById('kb-modal-overlay')) closeModal();
});

document.querySelectorAll('#kb-label-row .kb-label-dot').forEach(dot => {
dot.addEventListener('click', () => {
selectedLabel = dot.dataset.v;
document.querySelectorAll('#kb-label-row .kb-label-dot').forEach(d =>
d.classList.toggle('selected', d.dataset.v === selectedLabel));
});
});

document.getElementById('kb-modal-save').addEventListener('click', () => {
const title = document.getElementById('kb-input-title').value.trim();
if (!title) { document.getElementById('kb-input-title').focus(); return; }
const desc  = document.getElementById('kb-input-desc').value.trim();

if (modalMode === 'add') {
state.cards.push({ id: uid(), colId: modalColId, title, desc, label: selectedLabel });
showToast('Card added');
} else {
const card = state.cards.find(c => c.id === modalCardId);
if (card) { card.title = title; card.desc = desc; card.label = selectedLabel; }
showToast('Card updated');
}
save();
closeModal();
renderBoard();
});

/* Enter key in title saves */
document.getElementById('kb-input-title').addEventListener('keydown', e => {
if (e.key === 'Enter') { e.preventDefault(); document.getElementById('kb-modal-save').click(); }
});

document.getElementById('kb-modal-delete').addEventListener('click', () => {
if (!confirm('Delete this card?')) return;
state.cards = state.cards.filter(c => c.id !== modalCardId);
save();
closeModal();
renderBoard();
showToast('Card deleted');
});

/* ── Toolbar buttons ── */
document.getElementById('kb-btn-clear').addEventListener('click', () => {
if (!confirm('Clear all columns and cards? This cannot be undone.')) return;
state = { columns: [], cards: [] };
save();
renderBoard();
showToast('Board cleared');
});

document.getElementById('kb-btn-export').addEventListener('click', () => {
const json = JSON.stringify(state, null, 2);
const blob = new Blob([json], { type: 'application/json' });
const url  = URL.createObjectURL(blob);
const a    = document.createElement('a');
a.href     = url;
a.download = 'kanban-board.json';
a.click();
URL.revokeObjectURL(url);
showToast('Board exported');
});

document.getElementById('kb-btn-import').addEventListener('click', () => {
document.getElementById('kb-file-input').click();
});

document.getElementById('kb-file-input').addEventListener('change', e => {
const file = e.target.files[0];
if (!file) return;
const reader = new FileReader();
reader.onload = ev => {
try {
const parsed = JSON.parse(ev.target.result);
if (!parsed.columns || !parsed.cards) throw new Error('Invalid format');
state = parsed;
save();
renderBoard();
showToast('Board imported');
} catch (err) {
alert('Invalid JSON file. Please export from this tool first.');
}
};
reader.readAsText(file);
e.target.value = '';
});

/* ── Escape key closes modal ── */
document.addEventListener('keydown', e => {
if (e.key === 'Escape') closeModal();
});

/* ── HTML escape ── */
function escHtml(str) {
return String(str)
.replace(/&/g, '&amp;')
.replace(/</g, '&lt;')
.replace(/>/g, '&gt;')
.replace(/"/g, '&quot;')
.replace(/'/g, '&#39;');
}

/* ── Bootstrap ── */
load();
if (state.columns.length === 0) initDefault();
renderBoard();

})();
</script>

</div>

---

> Track habits alongside your tasks &rarr; [Habit Tracker](/tools/habit-tracker/)
> Focus with timed sessions &rarr; [Pomodoro Timer](/tools/pomodoro-timer/)
> Generate changelogs from your completed work &rarr; [Changelog Generator](/tools/changelog-generator/)

## Related Articles

- [Best Productivity Apps for Remote Workers 2026: Tested and Ranked](/posts/best-productivity-apps-remote-workers-2026/)
- [The Ultimate Notion Setup for Maximum Productivity](/posts/ultimate-notion-productivity-setup/)
- [Best Notion AI Templates for Productivity 2026](/posts/best-notion-ai-templates-for-productivity-2026/)
