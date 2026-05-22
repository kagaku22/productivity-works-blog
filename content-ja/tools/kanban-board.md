---
title: "カンバンボード"
date: 2025-05-05
description: "無料のカンバンボード。やること・進行中・完了のカラムでタスクを管理。ドラッグ＆ドロップ対応、データはローカル保存、会員登録不要。"
categories: ["無料ツール"]
tags: ["業務効率化", "生産性", "無料ツール"]
slug: "kanban-board"
ShowToc: false
cover:
  image: "/images/covers/kanban-board-ja.png"
  alt: "カンバンボード"
---

<div id="kb-app">

<style>
#kb-app *,
#kb-app *::before,
#kb-app *::after {
box-sizing: border-box;
margin: 0;
padding: 0;
}

#kb-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Hiragino Sans", "Noto Sans JP", sans-serif;
font-size: 14px;
color: #1e293b;
background: #f1f5f9;
border-radius: 12px;
padding: 20px;
min-height: 520px;
user-select: none;
}

/* ---- toolbar ---- */
#kb-app .kb-toolbar {
display: flex;
flex-wrap: wrap;
gap: 8px;
align-items: center;
margin-bottom: 16px;
}

#kb-app .kb-toolbar h2 {
font-size: 18px;
font-weight: 700;
color: #0f172a;
flex: 1 1 auto;
}

#kb-app .kb-btn {
display: inline-flex;
align-items: center;
gap: 4px;
padding: 7px 14px;
border-radius: 7px;
border: none;
cursor: pointer;
font-size: 13px;
font-weight: 600;
transition: background 0.15s, opacity 0.15s;
white-space: nowrap;
}

#kb-app .kb-btn:hover { opacity: 0.85; }

#kb-app .kb-btn-primary {
background: #0284c7;
color: #fff;
}

#kb-app .kb-btn-secondary {
background: #e2e8f0;
color: #334155;
}

#kb-app .kb-btn-success {
background: #16a34a;
color: #fff;
}

#kb-app .kb-btn-danger {
background: #dc2626;
color: #fff;
}

#kb-app .kb-btn-sm {
padding: 4px 10px;
font-size: 12px;
}

/* ---- board ---- */
#kb-app .kb-board {
display: flex;
gap: 14px;
overflow-x: auto;
padding-bottom: 8px;
align-items: flex-start;
}

/* ---- column ---- */
#kb-app .kb-col {
background: #e2e8f0;
border-radius: 10px;
min-width: 240px;
max-width: 280px;
flex: 0 0 260px;
display: flex;
flex-direction: column;
gap: 0;
transition: outline 0.1s;
}

#kb-app .kb-col.drag-over {
outline: 2px dashed #0284c7;
background: #dbeafe;
}

#kb-app .kb-col-header {
display: flex;
align-items: center;
gap: 6px;
padding: 10px 12px 8px;
border-bottom: 1px solid #cbd5e1;
}

#kb-app .kb-col-title {
flex: 1;
font-size: 13px;
font-weight: 700;
color: #0f172a;
cursor: pointer;
padding: 2px 4px;
border-radius: 4px;
word-break: break-all;
}

#kb-app .kb-col-title:hover {
background: #cbd5e1;
}

#kb-app .kb-col-title-input {
flex: 1;
font-size: 13px;
font-weight: 700;
color: #0f172a;
border: 1.5px solid #0284c7;
border-radius: 4px;
padding: 2px 4px;
outline: none;
background: #fff;
width: 100%;
}

#kb-app .kb-col-count {
background: #94a3b8;
color: #fff;
font-size: 11px;
font-weight: 700;
border-radius: 999px;
padding: 1px 7px;
min-width: 22px;
text-align: center;
}

#kb-app .kb-col-del {
background: none;
border: none;
cursor: pointer;
color: #94a3b8;
font-size: 16px;
line-height: 1;
padding: 0 2px;
border-radius: 4px;
}

#kb-app .kb-col-del:hover { color: #dc2626; background: #fee2e2; }

/* ---- cards list ---- */
#kb-app .kb-cards {
padding: 8px;
display: flex;
flex-direction: column;
gap: 8px;
min-height: 60px;
}

/* ---- card ---- */
#kb-app .kb-card {
background: #fff;
border-radius: 8px;
padding: 10px 12px;
cursor: grab;
box-shadow: 0 1px 3px rgba(0,0,0,0.08);
border-left: 4px solid transparent;
transition: box-shadow 0.15s, opacity 0.15s;
position: relative;
}

#kb-app .kb-card:active { cursor: grabbing; }

#kb-app .kb-card.dragging {
opacity: 0.4;
box-shadow: none;
}

#kb-app .kb-card-title {
font-size: 13px;
font-weight: 600;
color: #0f172a;
word-break: break-all;
line-height: 1.4;
}

#kb-app .kb-card-desc {
font-size: 12px;
color: #64748b;
margin-top: 4px;
word-break: break-all;
line-height: 1.4;
white-space: pre-wrap;
}

#kb-app .kb-card-footer {
display: flex;
align-items: center;
justify-content: space-between;
margin-top: 8px;
gap: 6px;
}

#kb-app .kb-card-label {
font-size: 10px;
font-weight: 700;
padding: 2px 8px;
border-radius: 999px;
letter-spacing: 0.02em;
}

#kb-app .kb-card-actions {
display: flex;
gap: 4px;
opacity: 0;
transition: opacity 0.15s;
}

#kb-app .kb-card:hover .kb-card-actions { opacity: 1; }

#kb-app .kb-card-btn {
background: none;
border: none;
cursor: pointer;
font-size: 13px;
padding: 2px 5px;
border-radius: 4px;
color: #64748b;
}

#kb-app .kb-card-btn:hover { background: #f1f5f9; color: #0f172a; }

/* ---- add card button ---- */
#kb-app .kb-add-card-btn {
margin: 4px 8px 10px;
background: none;
border: 1.5px dashed #94a3b8;
border-radius: 7px;
padding: 7px;
width: calc(100% - 16px);
cursor: pointer;
font-size: 12px;
color: #64748b;
font-weight: 600;
transition: background 0.15s, border-color 0.15s;
text-align: center;
}

#kb-app .kb-add-card-btn:hover {
background: #f8fafc;
border-color: #0284c7;
color: #0284c7;
}

/* ---- modal overlay ---- */
#kb-app .kb-overlay {
display: none;
position: fixed;
inset: 0;
background: rgba(15,23,42,0.45);
z-index: 9999;
align-items: center;
justify-content: center;
padding: 20px;
}

#kb-app .kb-overlay.open {
display: flex;
}

#kb-app .kb-modal {
background: #fff;
border-radius: 12px;
padding: 24px;
width: 100%;
max-width: 420px;
box-shadow: 0 20px 60px rgba(0,0,0,0.2);
display: flex;
flex-direction: column;
gap: 14px;
}

#kb-app .kb-modal h3 {
font-size: 16px;
font-weight: 700;
color: #0f172a;
}

#kb-app .kb-modal label {
font-size: 12px;
font-weight: 600;
color: #475569;
display: block;
margin-bottom: 4px;
}

#kb-app .kb-modal input[type="text"],
#kb-app .kb-modal textarea,
#kb-app .kb-modal select {
width: 100%;
border: 1.5px solid #cbd5e1;
border-radius: 7px;
padding: 8px 10px;
font-size: 13px;
color: #0f172a;
outline: none;
font-family: inherit;
transition: border-color 0.15s;
background: #f8fafc;
}

#kb-app .kb-modal input[type="text"]:focus,
#kb-app .kb-modal textarea:focus,
#kb-app .kb-modal select:focus {
border-color: #0284c7;
background: #fff;
}

#kb-app .kb-modal textarea {
resize: vertical;
min-height: 80px;
}

#kb-app .kb-modal-actions {
display: flex;
gap: 8px;
justify-content: flex-end;
}

/* ---- mobile move select ---- */
#kb-app .kb-move-select {
display: none;
margin-top: 6px;
width: 100%;
border: 1.5px solid #cbd5e1;
border-radius: 6px;
padding: 5px 8px;
font-size: 12px;
color: #334155;
background: #f8fafc;
font-family: inherit;
cursor: pointer;
}

/* ---- color label palette ---- */
#kb-app .kb-priority-row {
display: flex;
gap: 8px;
flex-wrap: wrap;
}

#kb-app .kb-priority-swatch {
display: flex;
align-items: center;
gap: 5px;
cursor: pointer;
}

#kb-app .kb-priority-swatch input[type="radio"] {
accent-color: #0284c7;
width: 14px;
height: 14px;
cursor: pointer;
}

#kb-app .kb-priority-dot {
width: 12px;
height: 12px;
border-radius: 50%;
display: inline-block;
}

#kb-app .kb-priority-swatch span {
font-size: 12px;
color: #334155;
}

/* ---- empty state ---- */
#kb-app .kb-empty {
text-align: center;
color: #94a3b8;
font-size: 12px;
padding: 12px 0 4px;
}

/* ---- responsive ---- */
@media (max-width: 600px) {
#kb-app .kb-board {
flex-direction: column;
overflow-x: unset;
}
#kb-app .kb-col {
min-width: unset;
max-width: unset;
flex: none;
width: 100%;
}
#kb-app .kb-card-actions {
opacity: 1;
}
#kb-app .kb-move-select {
display: block;
}
}
</style>

<!-- toolbar -->
<div class="kb-toolbar">
<h2>カンバンボード</h2>
<button class="kb-btn kb-btn-secondary" id="kb-import-btn" title="JSONから取込">&#8599; 取込</button>
<button class="kb-btn kb-btn-secondary" id="kb-export-btn" title="JSONで書き出し">&#8600; 書き出し</button>
<button class="kb-btn kb-btn-primary" id="kb-add-col-btn">＋ カラム追加</button>
</div>

<!-- board -->
<div class="kb-board" id="kb-board"></div>

<!-- card edit modal -->
<div class="kb-overlay" id="kb-modal-overlay">
<div class="kb-modal" role="dialog" aria-modal="true" aria-labelledby="kb-modal-title">
<h3 id="kb-modal-title">カードを追加</h3>
<div>
<label for="kb-input-title">タイトル</label>
<input type="text" id="kb-input-title" placeholder="タスクのタイトルを入力" maxlength="120" />
</div>
<div>
<label for="kb-input-desc">説明（任意）</label>
<textarea id="kb-input-desc" placeholder="詳細メモ..." maxlength="500"></textarea>
</div>
<div>
<label>優先度（色ラベル）</label>
<div class="kb-priority-row" id="kb-priority-row"></div>
</div>
<div class="kb-modal-actions">
<button class="kb-btn kb-btn-secondary" id="kb-modal-cancel">キャンセル</button>
<button class="kb-btn kb-btn-primary" id="kb-modal-save">保存</button>
</div>
</div>
</div>

<!-- confirm modal -->
<div class="kb-overlay" id="kb-confirm-overlay">
<div class="kb-modal" role="dialog" aria-modal="true">
<h3 id="kb-confirm-msg">削除しますか？</h3>
<div class="kb-modal-actions">
<button class="kb-btn kb-btn-secondary" id="kb-confirm-cancel">キャンセル</button>
<button class="kb-btn kb-btn-danger" id="kb-confirm-ok">削除</button>
</div>
</div>
</div>

<!-- hidden file input for import -->
<input type="file" id="kb-file-input" accept=".json" style="display:none" />

<script>
(function () {
'use strict';

/* ---- constants ---- */
const LS_KEY = 'kb_data_v2';

const PRIORITIES = [
{ key: 'none',   label: 'なし',    color: '#94a3b8', bg: '#f1f5f9', text: '#475569' },
{ key: 'low',    label: '低',      color: '#22c55e', bg: '#dcfce7', text: '#166534' },
{ key: 'mid',    label: '中',      color: '#f59e0b', bg: '#fef3c7', text: '#92400e' },
{ key: 'high',   label: '高',      color: '#ef4444', bg: '#fee2e2', text: '#991b1b' },
{ key: 'urgent', label: '緊急',    color: '#7c3aed', bg: '#ede9fe', text: '#4c1d95' },
];

const DEFAULT_COLS = [
{ id: uid(), title: 'やること',  cards: [
{ id: uid(), title: 'サンプルタスク', desc: 'カードをドラッグして移動できます', priority: 'mid' }
]},
{ id: uid(), title: '進行中',    cards: [] },
{ id: uid(), title: '完了',      cards: [] },
];

/* ---- state ---- */
let state = load();

/* ---- util ---- */
function uid() {
return Math.random().toString(36).slice(2, 10) + Date.now().toString(36);
}

function load() {
try {
const raw = localStorage.getItem(LS_KEY);
if (raw) return JSON.parse(raw);
} catch (_) {}
return { cols: DEFAULT_COLS };
}

function save() {
try { localStorage.setItem(LS_KEY, JSON.stringify(state)); } catch (_) {}
}

function getPriority(key) {
return PRIORITIES.find(p => p.key === key) || PRIORITIES[0];
}

/* ---- drag state ---- */
let dragCard = null;   // { cardId, srcColId }
let dragEl = null;

/* ---- render ---- */
function render() {
const board = document.getElementById('kb-board');
board.innerHTML = '';
state.cols.forEach(col => {
board.appendChild(makeColEl(col));
});
save();
}

function makeColEl(col) {
const el = document.createElement('div');
el.className = 'kb-col';
el.dataset.colId = col.id;

/* header */
const header = document.createElement('div');
header.className = 'kb-col-header';

const titleEl = document.createElement('span');
titleEl.className = 'kb-col-title';
titleEl.textContent = col.title;
titleEl.title = 'クリックして名前変更';
titleEl.addEventListener('click', () => startRenameCol(col.id, titleEl, countEl));

const countEl = document.createElement('span');
countEl.className = 'kb-col-count';
countEl.textContent = col.cards.length;

const delBtn = document.createElement('button');
delBtn.className = 'kb-col-del';
delBtn.title = 'カラムを削除';
delBtn.textContent = '×';
delBtn.addEventListener('click', () => confirmDeleteCol(col.id, col.title));

header.appendChild(titleEl);
header.appendChild(countEl);
header.appendChild(delBtn);
el.appendChild(header);

/* cards */
const cardsEl = document.createElement('div');
cardsEl.className = 'kb-cards';
cardsEl.dataset.colId = col.id;

if (col.cards.length === 0) {
const empty = document.createElement('p');
empty.className = 'kb-empty';
empty.textContent = 'タスクをここにドロップ';
cardsEl.appendChild(empty);
} else {
col.cards.forEach(card => {
cardsEl.appendChild(makeCardEl(card, col.id));
});
}

/* drop target */
cardsEl.addEventListener('dragover', e => {
e.preventDefault();
el.classList.add('drag-over');
});
cardsEl.addEventListener('dragleave', e => {
if (!el.contains(e.relatedTarget)) el.classList.remove('drag-over');
});
cardsEl.addEventListener('drop', e => {
e.preventDefault();
el.classList.remove('drag-over');
if (!dragCard) return;
moveCard(dragCard.cardId, dragCard.srcColId, col.id);
});

el.appendChild(cardsEl);

/* add card button */
const addBtn = document.createElement('button');
addBtn.className = 'kb-add-card-btn';
addBtn.textContent = '＋ カードを追加';
addBtn.addEventListener('click', () => openCardModal(col.id, null));
el.appendChild(addBtn);

return el;
}

function makeCardEl(card, colId) {
const pri = getPriority(card.priority);
const el = document.createElement('div');
el.className = 'kb-card';
el.style.borderLeftColor = pri.color;
el.draggable = true;
el.dataset.cardId = card.id;

el.addEventListener('dragstart', e => {
dragCard = { cardId: card.id, srcColId: colId };
dragEl = el;
setTimeout(() => el.classList.add('dragging'), 0);
});
el.addEventListener('dragend', () => {
el.classList.remove('dragging');
dragCard = null;
dragEl = null;
});

/* title */
const titleEl = document.createElement('div');
titleEl.className = 'kb-card-title';
titleEl.textContent = card.title;
el.appendChild(titleEl);

/* desc */
if (card.desc) {
const descEl = document.createElement('div');
descEl.className = 'kb-card-desc';
descEl.textContent = card.desc;
el.appendChild(descEl);
}

/* footer */
const footer = document.createElement('div');
footer.className = 'kb-card-footer';

/* label */
const labelEl = document.createElement('span');
labelEl.className = 'kb-card-label';
labelEl.textContent = pri.label;
labelEl.style.background = pri.bg;
labelEl.style.color = pri.text;
footer.appendChild(labelEl);

/* actions */
const actions = document.createElement('div');
actions.className = 'kb-card-actions';

const editBtn = document.createElement('button');
editBtn.className = 'kb-card-btn';
editBtn.title = '編集';
editBtn.textContent = '✏️';
editBtn.addEventListener('click', e => { e.stopPropagation(); openCardModal(colId, card.id); });

const delBtn = document.createElement('button');
delBtn.className = 'kb-card-btn';
delBtn.title = '削除';
delBtn.textContent = '🗑️';
delBtn.addEventListener('click', e => { e.stopPropagation(); confirmDeleteCard(colId, card.id, card.title); });

actions.appendChild(editBtn);
actions.appendChild(delBtn);
footer.appendChild(actions);
el.appendChild(footer);

/* mobile: move dropdown */
const moveSelect = document.createElement('select');
moveSelect.className = 'kb-move-select';
const placeholderOpt = document.createElement('option');
placeholderOpt.value = '';
placeholderOpt.textContent = '移動先カラムを選択...';
moveSelect.appendChild(placeholderOpt);
state.cols.forEach(c => {
if (c.id === colId) return;
const opt = document.createElement('option');
opt.value = c.id;
opt.textContent = c.title;
moveSelect.appendChild(opt);
});
moveSelect.addEventListener('change', () => {
if (moveSelect.value) {
moveCard(card.id, colId, moveSelect.value);
}
});
el.appendChild(moveSelect);

return el;
}

/* ---- card CRUD ---- */
let modalMode = null; // { colId, cardId|null }

function openCardModal(colId, cardId) {
modalMode = { colId, cardId };
const overlay = document.getElementById('kb-modal-overlay');
const titleInput = document.getElementById('kb-input-title');
const descInput = document.getElementById('kb-input-desc');
const modalTitle = document.getElementById('kb-modal-title');

/* build priority radios */
const row = document.getElementById('kb-priority-row');
row.innerHTML = '';
PRIORITIES.forEach(p => {
const label = document.createElement('label');
label.className = 'kb-priority-swatch';
const radio = document.createElement('input');
radio.type = 'radio';
radio.name = 'kb-priority';
radio.value = p.key;
const dot = document.createElement('span');
dot.className = 'kb-priority-dot';
dot.style.background = p.color;
const txt = document.createElement('span');
txt.textContent = p.label;
label.appendChild(radio);
label.appendChild(dot);
label.appendChild(txt);
row.appendChild(label);
});

if (cardId) {
modalTitle.textContent = 'カードを編集';
const col = state.cols.find(c => c.id === colId);
const card = col && col.cards.find(cd => cd.id === cardId);
if (card) {
titleInput.value = card.title;
descInput.value = card.desc || '';
const radio = row.querySelector(`input[value="${card.priority || 'none'}"]`);
if (radio) radio.checked = true;
}
} else {
modalTitle.textContent = 'カードを追加';
titleInput.value = '';
descInput.value = '';
const noneRadio = row.querySelector('input[value="none"]');
if (noneRadio) noneRadio.checked = true;
}

overlay.classList.add('open');
titleInput.focus();
}

function closeCardModal() {
document.getElementById('kb-modal-overlay').classList.remove('open');
modalMode = null;
}

function saveCard() {
if (!modalMode) return;
const title = document.getElementById('kb-input-title').value.trim();
if (!title) { document.getElementById('kb-input-title').focus(); return; }
const desc = document.getElementById('kb-input-desc').value.trim();
const checkedRadio = document.querySelector('#kb-priority-row input[name="kb-priority"]:checked');
const priority = checkedRadio ? checkedRadio.value : 'none';

const col = state.cols.find(c => c.id === modalMode.colId);
if (!col) return;

if (modalMode.cardId) {
const card = col.cards.find(cd => cd.id === modalMode.cardId);
if (card) { card.title = title; card.desc = desc; card.priority = priority; }
} else {
col.cards.push({ id: uid(), title, desc, priority });
}
closeCardModal();
render();
}

function moveCard(cardId, srcColId, dstColId) {
if (srcColId === dstColId) return;
const src = state.cols.find(c => c.id === srcColId);
const dst = state.cols.find(c => c.id === dstColId);
if (!src || !dst) return;
const idx = src.cards.findIndex(cd => cd.id === cardId);
if (idx === -1) return;
const [card] = src.cards.splice(idx, 1);
dst.cards.push(card);
render();
}

/* ---- column CRUD ---- */
function addCol() {
const title = prompt('新しいカラム名を入力してください:', '新カラム');
if (!title || !title.trim()) return;
state.cols.push({ id: uid(), title: title.trim(), cards: [] });
render();
}

function startRenameCol(colId, titleEl, countEl) {
const col = state.cols.find(c => c.id === colId);
if (!col) return;
const input = document.createElement('input');
input.type = 'text';
input.className = 'kb-col-title-input';
input.value = col.title;
titleEl.replaceWith(input);
input.focus();
input.select();

function commit() {
const newTitle = input.value.trim();
if (newTitle) col.title = newTitle;
render();
}
input.addEventListener('blur', commit);
input.addEventListener('keydown', e => {
if (e.key === 'Enter') { e.preventDefault(); commit(); }
if (e.key === 'Escape') render();
});
}

/* ---- confirm helpers ---- */
let confirmCb = null;

function showConfirm(msg, cb) {
document.getElementById('kb-confirm-msg').textContent = msg;
document.getElementById('kb-confirm-overlay').classList.add('open');
confirmCb = cb;
}

function closeConfirm() {
document.getElementById('kb-confirm-overlay').classList.remove('open');
confirmCb = null;
}

function confirmDeleteCard(colId, cardId, title) {
showConfirm(`「${title}」を削除しますか？`, () => {
const col = state.cols.find(c => c.id === colId);
if (col) col.cards = col.cards.filter(cd => cd.id !== cardId);
render();
});
}

function confirmDeleteCol(colId, title) {
showConfirm(`カラム「${title}」とそのすべてのカードを削除しますか？`, () => {
state.cols = state.cols.filter(c => c.id !== colId);
render();
});
}

/* ---- export / import ---- */
function exportJSON() {
const json = JSON.stringify(state, null, 2);
const blob = new Blob([json], { type: 'application/json' });
const url = URL.createObjectURL(blob);
const a = document.createElement('a');
a.href = url;
a.download = 'kanban-board.json';
a.click();
URL.revokeObjectURL(url);
}

function importJSON(file) {
if (!file) return;
const reader = new FileReader();
reader.onload = e => {
try {
const parsed = JSON.parse(e.target.result);
if (!parsed.cols || !Array.isArray(parsed.cols)) throw new Error('invalid');
state = parsed;
render();
} catch (_) {
alert('JSONの読み込みに失敗しました。正しいカンバンボードのJSONファイルを選択してください。');
}
};
reader.readAsText(file);
}

/* ---- touch support ---- */
let touchCard = null;
let touchSrcColId = null;
let touchGhost = null;

function setupTouchDrag(cardEl, cardId, colId) {
cardEl.addEventListener('touchstart', e => {
touchCard = { cardId, colId };
touchSrcColId = colId;
const touch = e.touches[0];
touchGhost = cardEl.cloneNode(true);
touchGhost.style.cssText = `
position:fixed;opacity:0.7;pointer-events:none;z-index:99999;
width:${cardEl.offsetWidth}px;left:${touch.clientX - cardEl.offsetWidth/2}px;
top:${touch.clientY - 20}px;background:#fff;border-radius:8px;
box-shadow:0 8px 24px rgba(0,0,0,0.18);padding:10px 12px;
`;
document.body.appendChild(touchGhost);
}, { passive: true });

cardEl.addEventListener('touchmove', e => {
if (!touchGhost) return;
const touch = e.touches[0];
touchGhost.style.left = (touch.clientX - parseInt(touchGhost.style.width)/2) + 'px';
touchGhost.style.top = (touch.clientY - 20) + 'px';
}, { passive: true });

cardEl.addEventListener('touchend', e => {
if (touchGhost) { document.body.removeChild(touchGhost); touchGhost = null; }
if (!touchCard) return;
const touch = e.changedTouches[0];
const target = document.elementFromPoint(touch.clientX, touch.clientY);
if (target) {
const colEl = target.closest('[data-col-id]');
if (colEl && colEl.dataset.colId !== touchSrcColId) {
moveCard(touchCard.cardId, touchSrcColId, colEl.dataset.colId);
}
}
touchCard = null;
});
}

/* override makeCardEl to also wire touch */
const _origMakeCardEl = makeCardEl;

/* ---- event wiring ---- */
document.getElementById('kb-add-col-btn').addEventListener('click', addCol);
document.getElementById('kb-export-btn').addEventListener('click', exportJSON);
document.getElementById('kb-import-btn').addEventListener('click', () => {
document.getElementById('kb-file-input').click();
});
document.getElementById('kb-file-input').addEventListener('change', e => {
importJSON(e.target.files[0]);
e.target.value = '';
});
document.getElementById('kb-modal-cancel').addEventListener('click', closeCardModal);
document.getElementById('kb-modal-save').addEventListener('click', saveCard);
document.getElementById('kb-modal-overlay').addEventListener('click', e => {
if (e.target === document.getElementById('kb-modal-overlay')) closeCardModal();
});
document.getElementById('kb-input-title').addEventListener('keydown', e => {
if (e.key === 'Enter') saveCard();
});
document.getElementById('kb-confirm-cancel').addEventListener('click', closeConfirm);
document.getElementById('kb-confirm-ok').addEventListener('click', () => {
if (confirmCb) confirmCb();
closeConfirm();
});
document.getElementById('kb-confirm-overlay').addEventListener('click', e => {
if (e.target === document.getElementById('kb-confirm-overlay')) closeConfirm();
});

/* ---- init ---- */
render();

})();
</script>

</div>

---

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業のタスク・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。無料トライアル実施中。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;width:fit-content;">freeeを無料で試す →</a>
</div>

---

> 習慣を記録 → [習慣トラッカー](/ja/tools/habit-tracker/)
> ポモドーロで集中 → [ポモドーロタイマー](/ja/tools/pomodoro-timer/)
> 変更履歴を作成 → [変更履歴ジェネレーター](/ja/tools/changelog-generator/)

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

## 関連記事

- [Notion使い方完全ガイド2026年版【初心者向けセットアップ解説】](/ja/posts/notion-kanzen-guide-shoshinsha-2026/)
- [Notion 使い方 完全ガイド【2026年版・初心者向け】セットアップから活用術まで](/ja/posts/notion-tsukaikata-shoshinsha-2026/)
