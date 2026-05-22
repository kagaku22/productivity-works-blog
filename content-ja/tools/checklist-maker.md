---
title: "チェックリスト作成ツール"
date: 2025-11-02
description: "無料のチェックリスト作成ツール。タスク管理・並べ替え・カテゴリ分類・進捗トラッキング。ブラウザ保存対応。"
categories: ["無料ツール"]
tags: ["業務効率化", "生産性", "無料ツール"]
slug: "checklist-maker"
ShowToc: false
cover:
  image: "/images/covers/checklist-maker-ja.png"
  alt: "チェックリスト作成ツール"
---

<div id="cl-app">
<style>
#cl-app *,#cl-app *::before,#cl-app *::after{box-sizing:border-box;margin:0;padding:0}
#cl-app{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Hiragino Sans,'Hiragino Kaku Gothic ProN','Noto Sans JP',sans-serif;max-width:720px;margin:0 auto;padding:16px;color:#1e293b}
#cl-app h2{font-size:1.25rem;font-weight:700;margin-bottom:12px;color:#0f172a}
#cl-app .cl-header{display:flex;align-items:center;gap:10px;margin-bottom:18px;flex-wrap:wrap}
#cl-app .cl-header h1{font-size:1.5rem;font-weight:800;color:#0f172a;flex:1}
#cl-app input[type="text"]{border:1.5px solid #cbd5e1;border-radius:7px;padding:8px 12px;font-size:14px;outline:none;transition:border-color .2s;background:#fff;color:#1e293b}
#cl-app input[type="text"]:focus{border-color:#3b82f6}
#cl-app button{border:none;border-radius:7px;padding:8px 14px;font-size:13px;font-weight:600;cursor:pointer;transition:background .15s,transform .1s}
#cl-app button:active{transform:scale(.97)}
#cl-app .btn-primary{background:#3b82f6;color:#fff}
#cl-app .btn-primary:hover{background:#2563eb}
#cl-app .btn-secondary{background:#e2e8f0;color:#475569}
#cl-app .btn-secondary:hover{background:#cbd5e1}
#cl-app .btn-danger{background:#fee2e2;color:#dc2626}
#cl-app .btn-danger:hover{background:#fecaca}
#cl-app .btn-sm{padding:4px 10px;font-size:12px}
#cl-app .cl-top-bar{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:14px;align-items:center}
#cl-app .cl-search{flex:1;min-width:160px}
#cl-app .cl-list-tabs{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:12px}
#cl-app .cl-tab{padding:6px 14px;border-radius:20px;font-size:13px;font-weight:600;cursor:pointer;border:1.5px solid #cbd5e1;background:#fff;color:#475569;transition:all .15s}
#cl-app .cl-tab.active{background:#3b82f6;color:#fff;border-color:#3b82f6}
#cl-app .cl-new-list{display:flex;gap:6px;margin-bottom:14px;flex-wrap:wrap}
#cl-app .cl-progress-bar-wrap{background:#e2e8f0;border-radius:99px;height:10px;margin-bottom:14px;overflow:hidden}
#cl-app .cl-progress-bar{background:linear-gradient(90deg,#3b82f6,#06b6d4);height:100%;border-radius:99px;transition:width .3s}
#cl-app .cl-progress-label{font-size:12px;color:#64748b;margin-bottom:8px}
#cl-app .cl-add-row{display:flex;gap:8px;margin-bottom:14px;flex-wrap:wrap}
#cl-app .cl-add-row input{flex:1;min-width:160px}
#cl-app .cl-list{list-style:none;display:flex;flex-direction:column;gap:6px}
#cl-app .cl-item{display:flex;align-items:center;gap:8px;background:#fff;border:1.5px solid #e2e8f0;border-radius:9px;padding:10px 12px;transition:box-shadow .15s,opacity .2s;cursor:grab;user-select:none}
#cl-app .cl-item:active{cursor:grabbing}
#cl-app .cl-item.dragging{opacity:.4;box-shadow:0 4px 16px rgba(59,130,246,.15)}
#cl-app .cl-item.drag-over{border-color:#3b82f6;background:#eff6ff}
#cl-app .cl-item.done .cl-item-text{text-decoration:line-through;color:#94a3b8}
#cl-app .cl-item-drag{color:#94a3b8;font-size:16px;cursor:grab;flex-shrink:0}
#cl-app .cl-item input[type="checkbox"]{width:17px;height:17px;accent-color:#3b82f6;cursor:pointer;flex-shrink:0}
#cl-app .cl-item-text{flex:1;font-size:14px;word-break:break-word}
#cl-app .cl-item-edit{flex:1;font-size:14px;border:none;outline:none;background:transparent;color:#1e293b}
#cl-app .cl-item-cat{font-size:11px;padding:2px 8px;border-radius:20px;background:#dbeafe;color:#1d4ed8;font-weight:600;flex-shrink:0}
#cl-app .cl-item-actions{display:flex;gap:4px;flex-shrink:0}
#cl-app .cl-empty{text-align:center;color:#94a3b8;font-size:14px;padding:32px 0}
#cl-app .cl-footer-actions{display:flex;gap:8px;flex-wrap:wrap;margin-top:14px}
#cl-app .cl-cat-group-label{font-size:12px;font-weight:700;color:#3b82f6;margin-top:10px;margin-bottom:4px;padding-left:4px}
@media(max-width:480px){
#cl-app .cl-header h1{font-size:1.2rem}
#cl-app .cl-add-row{flex-direction:column}
#cl-app .cl-footer-actions{flex-direction:column}
}
</style>

<div class="cl-header">
<h1>チェックリスト作成ツール</h1>
</div>

<div class="cl-top-bar">
<input type="text" id="cl-search" class="cl-search" placeholder="アイテムを検索..." oninput="clRender()">
<button class="btn-secondary btn-sm" onclick="clExport()">テキストで出力</button>
<button class="btn-danger btn-sm" onclick="clClearCompleted()">完了済みを削除</button>
</div>

<div class="cl-new-list" id="cl-new-list-row">
<input type="text" id="cl-new-list-name" placeholder="新しいリスト名..." style="width:200px">
<button class="btn-primary btn-sm" onclick="clAddList()">+ リストを追加</button>
</div>

<div id="cl-tabs" class="cl-list-tabs"></div>

<div class="cl-progress-label" id="cl-progress-label"></div>
<div class="cl-progress-bar-wrap"><div class="cl-progress-bar" id="cl-progress-bar" style="width:0%"></div></div>

<div class="cl-add-row">
<input type="text" id="cl-new-item" placeholder="アイテムを追加..." onkeydown="if(event.key==='Enter')clAddItem()">
<input type="text" id="cl-new-cat" placeholder="カテゴリ（任意）" style="width:160px">
<button class="btn-primary" onclick="clAddItem()">+ 追加</button>
</div>

<ul class="cl-list" id="cl-list"></ul>
<div id="cl-empty" class="cl-empty" style="display:none">アイテムがありません。上から追加してください！</div>

<div class="cl-footer-actions">
<button class="btn-danger btn-sm" onclick="clDeleteList()">このリストを削除</button>
</div>

<script>
(function(){
var STORE_KEY='cl_app_ja_v1';
var state={lists:[],activeList:0};

function load(){
try{var s=localStorage.getItem(STORE_KEY);if(s)state=JSON.parse(s);}catch(e){}
if(!state.lists||!state.lists.length){
state={lists:[{name:'マイチェックリスト',items:[]}],activeList:0};
}
if(state.activeList>=state.lists.length)state.activeList=0;
}

function save(){
try{localStorage.setItem(STORE_KEY,JSON.stringify(state));}catch(e){}
}

function currentList(){return state.lists[state.activeList];}

function clAddList(){
var n=document.getElementById('cl-new-list-name');
var name=(n.value||'').trim();
if(!name)return;
state.lists.push({name:name,items:[]});
state.activeList=state.lists.length-1;
n.value='';
save();clRender();
}
window.clAddList=clAddList;

function clDeleteList(){
if(state.lists.length<=1){alert('最後のリストは削除できません。');return;}
if(!confirm('このリストとすべてのアイテムを削除しますか？'))return;
state.lists.splice(state.activeList,1);
if(state.activeList>=state.lists.length)state.activeList=state.lists.length-1;
save();clRender();
}
window.clDeleteList=clDeleteList;

function clSwitchList(i){
state.activeList=i;
save();clRender();
}
window.clSwitchList=clSwitchList;

function clAddItem(){
var n=document.getElementById('cl-new-item');
var c=document.getElementById('cl-new-cat');
var text=(n.value||'').trim();
if(!text)return;
currentList().items.push({id:Date.now()+'_'+Math.random(),text:text,done:false,cat:(c.value||'').trim()});
n.value='';c.value='';
save();clRender();
}
window.clAddItem=clAddItem;

function clToggle(id){
var item=currentList().items.find(function(x){return x.id===id;});
if(item)item.done=!item.done;
save();clRender();
}
window.clToggle=clToggle;

function clDelete(id){
var list=currentList();
list.items=list.items.filter(function(x){return x.id!==id;});
save();clRender();
}
window.clDelete=clDelete;

function clStartEdit(id){
var el=document.getElementById('cl-text-'+id);
var input=document.getElementById('cl-edit-'+id);
if(!el||!input)return;
el.style.display='none';
input.style.display='block';
input.focus();
input.select();
}
window.clStartEdit=clStartEdit;

function clFinishEdit(id){
var input=document.getElementById('cl-edit-'+id);
var el=document.getElementById('cl-text-'+id);
if(!input||!el)return;
var item=currentList().items.find(function(x){return x.id===id;});
if(item){item.text=input.value.trim()||item.text;}
el.style.display='';
input.style.display='none';
save();clRender();
}
window.clFinishEdit=clFinishEdit;

function clClearCompleted(){
var list=currentList();
list.items=list.items.filter(function(x){return !x.done;});
save();clRender();
}
window.clClearCompleted=clClearCompleted;

function clExport(){
var list=currentList();
var lines=[list.name,''];
var cats={};
list.items.forEach(function(item){
var c=item.cat||'';
if(!cats[c])cats[c]=[];
cats[c].push(item);
});
Object.keys(cats).forEach(function(cat){
if(cat)lines.push('['+cat+']');
cats[cat].forEach(function(item){
lines.push((item.done?'[完] ':'[ ] ')+item.text);
});
lines.push('');
});
var blob=new Blob([lines.join('\n')],{type:'text/plain'});
var a=document.createElement('a');
a.href=URL.createObjectURL(blob);
a.download=(list.name||'checklist')+'.txt';
a.click();
URL.revokeObjectURL(a.href);
}
window.clExport=clExport;

// Drag and drop
var dragSrcId=null;

function clDragStart(id){dragSrcId=id;}
window.clDragStart=clDragStart;

function clDragOver(e,id){
e.preventDefault();
document.querySelectorAll('#cl-app .cl-item').forEach(function(el){el.classList.remove('drag-over');});
var el=document.getElementById('cl-li-'+id);
if(el)el.classList.add('drag-over');
}
window.clDragOver=clDragOver;

function clDrop(id){
if(!dragSrcId||dragSrcId===id)return;
var items=currentList().items;
var srcIdx=items.findIndex(function(x){return x.id===dragSrcId;});
var dstIdx=items.findIndex(function(x){return x.id===id;});
if(srcIdx<0||dstIdx<0)return;
var removed=items.splice(srcIdx,1)[0];
items.splice(dstIdx,0,removed);
dragSrcId=null;
save();clRender();
}
window.clDrop=clDrop;

function clDragEnd(){
dragSrcId=null;
document.querySelectorAll('#cl-app .cl-item').forEach(function(el){el.classList.remove('drag-over','dragging');});
}
window.clDragEnd=clDragEnd;

function clRender(){
var list=currentList();
var search=(document.getElementById('cl-search')||{}).value||'';
var sq=search.trim().toLowerCase();

// Tabs
var tabsEl=document.getElementById('cl-tabs');
tabsEl.innerHTML='';
state.lists.forEach(function(l,i){
var btn=document.createElement('button');
btn.className='cl-tab'+(i===state.activeList?' active':'');
btn.textContent=l.name;
btn.onclick=function(){clSwitchList(i);};
tabsEl.appendChild(btn);
});

// Progress
var total=list.items.length;
var done=list.items.filter(function(x){return x.done;}).length;
var pct=total?Math.round(done/total*100):0;
document.getElementById('cl-progress-label').textContent=total?done+' / '+total+' 完了 ('+pct+'%)':'アイテムなし';
document.getElementById('cl-progress-bar').style.width=pct+'%';

// Filter
var filtered=list.items.filter(function(item){
return !sq||(item.text.toLowerCase().includes(sq)||(item.cat||'').toLowerCase().includes(sq));
});

// Group by category
var cats={};
var catOrder=[];
filtered.forEach(function(item){
var c=item.cat||'';
if(!cats[c]){cats[c]=[];catOrder.push(c);}
cats[c].push(item);
});

var ul=document.getElementById('cl-list');
var emptyEl=document.getElementById('cl-empty');
ul.innerHTML='';

if(!filtered.length){
emptyEl.style.display='';
} else {
emptyEl.style.display='none';
catOrder.forEach(function(cat){
if(cat){
var lbl=document.createElement('li');
lbl.className='cl-cat-group-label';
lbl.textContent=cat;
ul.appendChild(lbl);
}
cats[cat].forEach(function(item){
var li=document.createElement('li');
li.className='cl-item'+(item.done?' done':'');
li.id='cl-li-'+item.id;
li.draggable=true;
li.ondragstart=function(){li.classList.add('dragging');clDragStart(item.id);};
li.ondragover=function(e){clDragOver(e,item.id);};
li.ondrop=function(){clDrop(item.id);};
li.ondragend=clDragEnd;

li.innerHTML=
'<span class="cl-item-drag" title="ドラッグして並べ替え">&#8942;&#8942;</span>'+
'<input type="checkbox"'+(item.done?' checked':'')+' onchange="clToggle(\''+item.id+'\')">'+
'<span class="cl-item-text" id="cl-text-'+item.id+'" ondblclick="clStartEdit(\''+item.id+'\')">'+escHtml(item.text)+'</span>'+
'<input type="text" class="cl-item-edit" id="cl-edit-'+item.id+'" value="'+escHtml(item.text)+'" style="display:none" onblur="clFinishEdit(\''+item.id+'\')" onkeydown="if(event.key===\'Enter\')clFinishEdit(\''+item.id+'\')">'+
(item.cat?'<span class="cl-item-cat">'+escHtml(item.cat)+'</span>':'')+
'<span class="cl-item-actions">'+
'<button class="btn-secondary btn-sm" onclick="clStartEdit(\''+item.id+'\')">編集</button>'+
'<button class="btn-danger btn-sm" onclick="clDelete(\''+item.id+'\')">削除</button>'+
'</span>';
ul.appendChild(li);
});
});
}
}

function escHtml(s){
return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;').replace(/'/g,'&#39;');
}

load();
clRender();
})();
</script>

---

> カンバンボード -> [カンバンボード](/ja/tools/kanban-board/)

> デイリープランナー -> [デイリープランナー](/ja/tools/daily-planner/)

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。

<div style="margin-top:28px;padding:18px 20px;background:linear-gradient(135deg,#f0f9ff 0%,#e0f2fe 100%);border:1.5px solid #bae6fd;border-radius:10px;">
<p style="margin:0;font-size:14px;color:#0369a1;font-weight:600;">事業の請求書・経費管理もかんたんに</p>
<span style="font-size:13px;color:#0c4a6e;">freee会計なら、請求書作成・経費精算・確定申告までクラウドで一元管理。</span>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener" style="display:inline-block;margin-top:4px;padding:9px 20px;background:#0284c7;color:#fff;border-radius:7px;font-size:13px;font-weight:700;text-decoration:none;">freeeを無料で試す &rarr;</a>
</div>

</div>

## 関連記事

- [Notion 使い方 完全ガイド【2026年版・初心者向け】セットアップから活用術まで](/ja/posts/notion-tsukaikata-shoshinsha-2026/)
