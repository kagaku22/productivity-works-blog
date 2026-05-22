---
title: "Gitコマンドジェネレーター — クイックリファレンス"
date: 2025-05-26
description: "シナリオ別にGitコマンドを生成。コミット取消・ブランチ作成・コンフリクト解消など一般的なワークフローを検索。コマンドをワンクリックコピー。"
categories: ["無料ツール"]
tags: ["開発ツール", "ドキュメント", "無料ツール"]
slug: "git-command-generator"
ShowToc: false
aliases:
  - "/ja/tools/git-command-generator/"
  - "/ja/tools/git-command-generator/"
cover:
  image: "/images/covers/git-command-generator-ja.png"
  alt: "Gitコマンドジェネレーター"
---

シナリオを選ぶだけで、正確な git コマンドとフラグの解説をすぐに確認できます。ワンクリックでコピー。登録不要・無料。

<div id="git-app">
<style>
#git-app *,
#git-app *::before,
#git-app *::after {
box-sizing: border-box;
}
#git-app {
font-family: "Hiragino Kaku Gothic ProN", "Hiragino Sans", Meiryo, -apple-system, BlinkMacSystemFont, sans-serif;
font-size: 15px;
color: #1a1a2e;
margin: 0 auto;
max-width: 960px;
}

/* Search */
#git-app .git-search-wrap {
margin-bottom: 20px;
}
#git-app #git-search {
width: 100%;
padding: 11px 16px;
border: 2px solid #e2e8f0;
border-radius: 10px;
font-size: 1rem;
font-family: inherit;
background: #fff;
color: #1a1a2e;
outline: none;
transition: border-color 0.18s;
}
#git-app #git-search:focus {
border-color: #f05033;
}
#git-app .git-search-count {
margin-top: 6px;
font-size: 0.82rem;
color: #718096;
}

/* Category tabs */
#git-app .git-tabs {
display: flex;
flex-wrap: wrap;
gap: 8px;
margin-bottom: 22px;
}
#git-app .git-tab {
padding: 7px 16px;
border-radius: 20px;
border: 2px solid #e2e8f0;
background: #fff;
font-size: 0.88rem;
font-weight: 600;
color: #4a5568;
cursor: pointer;
transition: all 0.15s;
font-family: inherit;
}
#git-app .git-tab:hover {
border-color: #f05033;
color: #f05033;
}
#git-app .git-tab.active {
background: #f05033;
border-color: #f05033;
color: #fff;
}

/* Layout: sidebar + main */
#git-app .git-layout {
display: flex;
gap: 20px;
align-items: flex-start;
}
#git-app .git-sidebar {
width: 230px;
flex-shrink: 0;
}
#git-app .git-main {
flex: 1;
min-width: 0;
}

/* Scenario list */
#git-app .git-scenario-list {
background: #f8f9fc;
border: 1px solid #e2e8f0;
border-radius: 10px;
overflow: hidden;
}
#git-app .git-scenario-item {
padding: 10px 14px;
border-bottom: 1px solid #e2e8f0;
cursor: pointer;
font-size: 0.88rem;
color: #2d3748;
transition: background 0.12s;
display: flex;
align-items: center;
gap: 8px;
line-height: 1.4;
}
#git-app .git-scenario-item:last-child {
border-bottom: none;
}
#git-app .git-scenario-item:hover {
background: #fff0ee;
color: #f05033;
}
#git-app .git-scenario-item.active {
background: #f05033;
color: #fff;
font-weight: 600;
}
#git-app .git-scenario-item .git-badge {
font-size: 0.72rem;
padding: 2px 6px;
border-radius: 10px;
background: rgba(255,255,255,0.25);
margin-left: auto;
flex-shrink: 0;
}
#git-app .git-scenario-item:not(.active) .git-badge {
background: #edf2f7;
color: #718096;
}

/* Command output panel */
#git-app .git-output {
background: #f8f9fc;
border: 1px solid #e2e8f0;
border-radius: 10px;
overflow: hidden;
min-height: 320px;
}
#git-app .git-output-header {
background: #fff;
border-bottom: 1px solid #e2e8f0;
padding: 14px 18px;
display: flex;
align-items: center;
justify-content: space-between;
gap: 12px;
flex-wrap: wrap;
}
#git-app .git-output-title {
font-size: 1rem;
font-weight: 700;
color: #1a1a2e;
}
#git-app .git-cat-label {
font-size: 0.76rem;
font-weight: 600;
padding: 3px 10px;
border-radius: 12px;
background: #fff0ee;
color: #f05033;
letter-spacing: 0.02em;
}
#git-app .git-output-body {
padding: 18px;
}
#git-app .git-desc {
font-size: 0.92rem;
color: #4a5568;
margin-bottom: 16px;
line-height: 1.65;
}

/* Command block */
#git-app .git-cmd-block {
background: #1a1a2e;
border-radius: 8px;
overflow: hidden;
margin-bottom: 16px;
}
#git-app .git-cmd-topbar {
display: flex;
align-items: center;
justify-content: space-between;
padding: 8px 14px;
background: #12121f;
border-bottom: 1px solid #2d2d44;
}
#git-app .git-cmd-label {
font-size: 0.75rem;
color: #a0aec0;
font-family: monospace;
letter-spacing: 0.04em;
}
#git-app .git-copy-btn {
padding: 4px 12px;
background: #f05033;
color: #fff;
border: none;
border-radius: 5px;
font-size: 0.78rem;
font-weight: 600;
cursor: pointer;
transition: background 0.15s;
font-family: inherit;
}
#git-app .git-copy-btn:hover {
background: #d03e25;
}
#git-app .git-copy-btn.copied {
background: #38a169;
}
#git-app .git-cmd-code {
padding: 14px 16px;
font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
font-size: 0.92rem;
color: #e2e8f0;
white-space: pre-wrap;
word-break: break-all;
line-height: 1.6;
}
#git-app .git-cmd-code .git-flag {
color: #f6ad55;
}
#git-app .git-cmd-code .git-placeholder {
color: #68d391;
font-style: italic;
}
#git-app .git-cmd-code .git-keyword {
color: #63b3ed;
}

/* Flags table */
#git-app .git-flags-title {
font-size: 0.82rem;
font-weight: 700;
color: #4a5568;
letter-spacing: 0.02em;
margin-bottom: 10px;
}
#git-app .git-flags-table {
width: 100%;
border-collapse: collapse;
font-size: 0.87rem;
}
#git-app .git-flags-table th {
text-align: left;
padding: 6px 10px;
background: #edf2f7;
color: #4a5568;
font-weight: 600;
border-bottom: 1px solid #e2e8f0;
}
#git-app .git-flags-table td {
padding: 7px 10px;
border-bottom: 1px solid #e2e8f0;
color: #2d3748;
vertical-align: top;
}
#git-app .git-flags-table tr:last-child td {
border-bottom: none;
}
#git-app .git-flags-table code {
font-family: monospace;
background: #edf2f7;
padding: 1px 5px;
border-radius: 4px;
font-size: 0.85rem;
color: #c05621;
}

/* Variants */
#git-app .git-variants {
margin-top: 16px;
}
#git-app .git-variants-title {
font-size: 0.82rem;
font-weight: 700;
color: #4a5568;
letter-spacing: 0.02em;
margin-bottom: 10px;
}
#git-app .git-variant-item {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 7px;
padding: 10px 14px;
margin-bottom: 8px;
display: flex;
align-items: flex-start;
gap: 12px;
}
#git-app .git-variant-cmd {
font-family: monospace;
font-size: 0.87rem;
color: #2d3748;
background: #f8f9fc;
padding: 4px 8px;
border-radius: 5px;
flex-shrink: 0;
}
#git-app .git-variant-desc {
font-size: 0.85rem;
color: #718096;
line-height: 1.5;
}

/* Placeholder state */
#git-app .git-placeholder-state {
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
min-height: 280px;
color: #a0aec0;
text-align: center;
gap: 12px;
}
#git-app .git-placeholder-state .git-icon-big {
font-size: 2.8rem;
}
#git-app .git-placeholder-state p {
font-size: 0.92rem;
max-width: 280px;
line-height: 1.6;
}

/* Workflows section */
#git-app .git-workflows {
margin-top: 28px;
background: #f8f9fc;
border: 1px solid #e2e8f0;
border-radius: 10px;
padding: 18px 20px;
}
#git-app .git-workflows-title {
font-size: 1rem;
font-weight: 700;
margin-bottom: 14px;
color: #1a1a2e;
display: flex;
align-items: center;
gap: 8px;
}
#git-app .git-workflow-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
gap: 12px;
}
#git-app .git-workflow-card {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 8px;
padding: 14px;
cursor: pointer;
transition: border-color 0.15s, box-shadow 0.15s;
}
#git-app .git-workflow-card:hover {
border-color: #f05033;
box-shadow: 0 2px 8px rgba(240,80,51,0.1);
}
#git-app .git-workflow-card h4 {
font-size: 0.9rem;
font-weight: 700;
margin: 0 0 6px 0;
color: #2d3748;
}
#git-app .git-workflow-card p {
font-size: 0.82rem;
color: #718096;
margin: 0 0 10px 0;
line-height: 1.5;
}
#git-app .git-workflow-cmd {
font-family: monospace;
font-size: 0.8rem;
background: #1a1a2e;
color: #e2e8f0;
padding: 6px 10px;
border-radius: 5px;
display: block;
white-space: pre-wrap;
word-break: break-all;
line-height: 1.5;
}
#git-app .git-workflow-footer {
margin-top: 10px;
display: flex;
justify-content: flex-end;
}
#git-app .git-workflow-copy {
font-size: 0.78rem;
color: #f05033;
background: none;
border: 1px solid #f05033;
border-radius: 5px;
padding: 3px 10px;
cursor: pointer;
font-weight: 600;
transition: all 0.14s;
font-family: inherit;
}
#git-app .git-workflow-copy:hover {
background: #f05033;
color: #fff;
}
#git-app .git-workflow-copy.copied {
background: #38a169;
border-color: #38a169;
color: #fff;
}

/* No results */
#git-app .git-no-results {
text-align: center;
padding: 30px;
color: #a0aec0;
font-size: 0.92rem;
}

/* freee CTA */
#git-app .git-cta {
margin-top: 28px;
background: linear-gradient(135deg, #fff0ee 0%, #fff8f7 100%);
border: 1px solid #fcd5cc;
border-radius: 10px;
padding: 20px;
display: flex;
align-items: flex-start;
gap: 16px;
}
#git-app .git-cta-icon {
font-size: 2rem;
flex-shrink: 0;
margin-top: 2px;
}
#git-app .git-cta-body strong {
font-size: 0.97rem;
font-weight: 700;
color: #1a1a2e;
display: block;
margin-bottom: 5px;
}
#git-app .git-cta-body p {
font-size: 0.87rem;
color: #4a5568;
margin: 0 0 12px 0;
line-height: 1.6;
}
#git-app .git-cta-link {
display: inline-block;
padding: 8px 18px;
background: #f05033;
color: #fff;
border-radius: 7px;
font-size: 0.88rem;
font-weight: 700;
text-decoration: none;
transition: background 0.15s;
}
#git-app .git-cta-link:hover {
background: #d03e25;
}

/* Responsive */
@media (max-width: 680px) {
#git-app .git-layout {
flex-direction: column;
}
#git-app .git-sidebar {
width: 100%;
}
#git-app .git-scenario-list {
display: grid;
grid-template-columns: 1fr 1fr;
}
#git-app .git-scenario-item {
border-right: 1px solid #e2e8f0;
}
#git-app .git-workflow-grid {
grid-template-columns: 1fr;
}
#git-app .git-tabs {
gap: 6px;
}
#git-app .git-tab {
font-size: 0.82rem;
padding: 6px 12px;
}
}
</style>

<!-- 検索 -->
<div class="git-search-wrap">
<input type="text" id="git-search" placeholder="シナリオを検索... 例: undo, branch, rebase, 取消" autocomplete="off" />
<div class="git-search-count" id="git-search-count"></div>
</div>

<!-- カテゴリタブ -->
<div class="git-tabs" id="git-tabs"></div>

<!-- レイアウト -->
<div class="git-layout">
<div class="git-sidebar">
<div class="git-scenario-list" id="git-scenario-list"></div>
</div>
<div class="git-main">
<div class="git-output" id="git-output">
<div class="git-placeholder-state">
<div class="git-icon-big">&#9881;</div>
<p>左のパネルからシナリオを選ぶと、コマンドと解説が表示されます。</p>
</div>
</div>
</div>
</div>

<!-- よくあるワークフロー -->
<div class="git-workflows" id="git-workflows">
<div class="git-workflows-title">&#9889; よくあるワークフロー</div>
<div class="git-workflow-grid" id="git-workflow-grid"></div>
</div>

<!-- freee CTA -->
<div class="git-cta">
<div class="git-cta-icon">&#128200;</div>
<div class="git-cta-body">
<strong>開発チームの経費・請求書・給与計算もまとめて効率化</strong>
<p>freee なら経費精算・請求書発行・給与計算をクラウドで自動化。エンジニアチームのバックオフィス業務をスリムにできます。無料プランから始められます。</p>
<a class="git-cta-link" href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" target="_blank" rel="noopener">freee を無料で試す</a>
</div>
</div>

<script>
(function () {
'use strict';

/* ── データ定義 ────────────────────────────────────────────────── */
var CATEGORIES = [
{ id: 'all',      label: 'すべて' },
{ id: 'basic',    label: '基本操作' },
{ id: 'branch',   label: 'ブランチ' },
{ id: 'undo',     label: '取消・修正' },
{ id: 'remote',   label: 'リモート' },
{ id: 'advanced', label: '応用' },
];

var SCENARIOS = [
/* ── 基本操作 ── */
{
id: 'init', cat: 'basic',
label: 'リポジトリを初期化する',
desc: 'カレントディレクトリに新しい Git リポジトリを作成します。隠しフォルダ .git が作られ、変更履歴の追跡が始まります。',
cmd: 'git init',
cmdDisplay: '<span class="git-keyword">git</span> init',
flags: [],
variants: [
{ cmd: 'git init <ディレクトリ名>', desc: '指定ディレクトリを作成してそこで初期化する' },
{ cmd: 'git init --bare', desc: 'ベアリポジトリを作成（作業ツリーなし・リモートサーバー用）' },
]
},
{
id: 'clone', cat: 'basic',
label: 'リポジトリをクローンする',
desc: 'リモート URL からリポジトリをダウンロードし、完全な履歴を持つローカルコピーを作成します。',
cmd: 'git clone <URL>',
cmdDisplay: '<span class="git-keyword">git</span> clone <span class="git-placeholder">&lt;URL&gt;</span>',
flags: [],
variants: [
{ cmd: 'git clone <URL> <ディレクトリ名>', desc: '指定した名前のディレクトリにクローンする' },
{ cmd: 'git clone --depth 1 <URL>', desc: 'シャロークローン — 最新のスナップショットのみ（高速）' },
{ cmd: 'git clone -b <ブランチ名> <URL>', desc: '特定ブランチをチェックアウトしてクローンする' },
]
},
{
id: 'add-all', cat: 'basic',
label: '変更をすべてステージングする',
desc: 'ワーキングディレクトリ内の変更・新規ファイルをすべてステージングエリア（インデックス）に追加し、コミット準備を整えます。',
cmd: 'git add .',
cmdDisplay: '<span class="git-keyword">git</span> add <span class="git-flag">.</span>',
flags: [
{ flag: '.', desc: 'カレントディレクトリ以下の変更をすべてステージング' },
],
variants: [
{ cmd: 'git add -A', desc: 'リポジトリ全体の変更（削除含む）をすべてステージング' },
{ cmd: 'git add <ファイル名>', desc: '特定のファイルのみをステージング' },
{ cmd: 'git add -p', desc: '変更箇所を対話的に選んでステージング（パッチモード）' },
]
},
{
id: 'commit', cat: 'basic',
label: 'ステージした変更をコミットする',
desc: 'ステージングエリアの変更を、説明メッセージとともにリポジトリの履歴に保存します。',
cmd: 'git commit -m "コミットメッセージ"',
cmdDisplay: '<span class="git-keyword">git</span> commit <span class="git-flag">-m</span> <span class="git-placeholder">"コミットメッセージ"</span>',
flags: [
{ flag: '-m "<メッセージ>"', desc: 'コミットメッセージをインラインで指定する' },
],
variants: [
{ cmd: 'git commit -am "メッセージ"', desc: 'トラック済みファイルのステージングとコミットを一度に実行' },
{ cmd: 'git commit --amend -m "新しいメッセージ"', desc: '直前のコミットメッセージを修正（未プッシュ時のみ安全）' },
{ cmd: 'git commit --no-edit --amend', desc: 'メッセージを変えずに直前のコミットに変更を追加' },
]
},
{
id: 'status', cat: 'basic',
label: '作業ツリーの状態を確認する',
desc: 'ステージ済み・変更済み・未追跡のファイルを一覧表示します。',
cmd: 'git status',
cmdDisplay: '<span class="git-keyword">git</span> status',
flags: [],
variants: [
{ cmd: 'git status -s', desc: 'コンパクトな短縮表示形式' },
{ cmd: 'git status --ignored', desc: '無視されているファイルも表示する' },
]
},
{
id: 'log', cat: 'basic',
label: 'コミット履歴を見る',
desc: '作者・日付・メッセージとともに最近のコミットを一覧表示します。',
cmd: 'git log --oneline --graph --decorate',
cmdDisplay: '<span class="git-keyword">git</span> log <span class="git-flag">--oneline --graph --decorate</span>',
flags: [
{ flag: '--oneline', desc: '各コミットを1行に圧縮して表示' },
{ flag: '--graph', desc: 'ブランチのグラフを ASCII アートで左端に描画' },
{ flag: '--decorate', desc: 'ブランチ名・タグ名をコミットの隣に表示' },
],
variants: [
{ cmd: 'git log -n 10', desc: '直近10件のコミットのみ表示' },
{ cmd: 'git log --author="名前"', desc: '特定の作者のコミットだけ絞り込む' },
{ cmd: 'git log --since="2 weeks ago"', desc: '過去2週間のコミットを表示' },
{ cmd: 'git log -- <ファイル>', desc: '特定のファイルに関わるコミットのみ表示' },
]
},
{
id: 'diff', cat: 'basic',
label: '未ステージの変更を確認する',
desc: 'ワーキングディレクトリとインデックス（ステージングエリア）の差分を行単位で表示します。',
cmd: 'git diff',
cmdDisplay: '<span class="git-keyword">git</span> diff',
flags: [],
variants: [
{ cmd: 'git diff --staged', desc: 'ステージ済みの変更と直前のコミットとの差分を表示' },
{ cmd: 'git diff HEAD', desc: 'ステージ済み＋未ステージを含む全変更と直前コミットとの差分' },
{ cmd: 'git diff <ブランチA>..<ブランチB>', desc: '2つのブランチを比較する' },
]
},
/* ── ブランチ ── */
{
id: 'branch-create', cat: 'branch',
label: '新しいブランチを作成して切り替える',
desc: '現在のコミットを起点に新しいブランチを作成し、即座にそこへ切り替えます。',
cmd: 'git checkout -b <ブランチ名>',
cmdDisplay: '<span class="git-keyword">git</span> checkout <span class="git-flag">-b</span> <span class="git-placeholder">&lt;ブランチ名&gt;</span>',
flags: [
{ flag: '-b', desc: 'ブランチを作成し、同時にそこへ切り替える' },
],
variants: [
{ cmd: 'git switch -c <ブランチ名>', desc: '新しい構文（Git 2.23+）: 作成と切り替えを同時に' },
{ cmd: 'git branch <ブランチ名>', desc: '切り替えずにブランチだけ作成する' },
{ cmd: 'git checkout -b <ブランチ名> origin/<ブランチ名>', desc: 'リモートブランチを追跡するローカルブランチを作成' },
]
},
{
id: 'branch-switch', cat: 'branch',
label: 'ブランチを切り替える',
desc: '既存の別ブランチに HEAD を移動し、ワーキングディレクトリを更新します。',
cmd: 'git switch <ブランチ名>',
cmdDisplay: '<span class="git-keyword">git</span> switch <span class="git-placeholder">&lt;ブランチ名&gt;</span>',
flags: [],
variants: [
{ cmd: 'git checkout <ブランチ名>', desc: 'ブランチ切り替えの従来の構文' },
{ cmd: 'git switch -', desc: '直前にいたブランチに戻る' },
]
},
{
id: 'branch-merge', cat: 'branch',
label: 'ブランチをマージする',
desc: '別のブランチの変更をマージコミットを作成して現在のブランチに統合します。',
cmd: 'git merge <ブランチ名>',
cmdDisplay: '<span class="git-keyword">git</span> merge <span class="git-placeholder">&lt;ブランチ名&gt;</span>',
flags: [],
variants: [
{ cmd: 'git merge --no-ff <ブランチ>', desc: 'fast-forward 可能な場合でも必ずマージコミットを作成する' },
{ cmd: 'git merge --squash <ブランチ>', desc: 'ブランチの全コミットを1つにまとめてステージングする（自動コミットなし）' },
{ cmd: 'git merge --abort', desc: 'マージを中断してマージ前の状態に戻す' },
]
},
{
id: 'branch-delete', cat: 'branch',
label: 'ブランチを削除する',
desc: 'マージ済みのブランチをローカルから削除します。-D を使うと未マージでも強制削除できます。',
cmd: 'git branch -d <ブランチ名>',
cmdDisplay: '<span class="git-keyword">git</span> branch <span class="git-flag">-d</span> <span class="git-placeholder">&lt;ブランチ名&gt;</span>',
flags: [
{ flag: '-d', desc: 'ブランチを削除（安全 — マージ済みの場合のみ成功）' },
{ flag: '-D', desc: 'マージ未完了でも強制削除する' },
],
variants: [
{ cmd: 'git push origin --delete <ブランチ名>', desc: 'リモートブランチを削除する' },
{ cmd: 'git branch -D <ブランチ名>', desc: 'マージ状態に関係なくローカルブランチを強制削除' },
]
},
{
id: 'branch-list', cat: 'branch',
label: 'すべてのブランチを一覧表示する',
desc: 'ローカルおよびリモートの全ブランチを表示します。現在のブランチはハイライトされます。',
cmd: 'git branch -a',
cmdDisplay: '<span class="git-keyword">git</span> branch <span class="git-flag">-a</span>',
flags: [
{ flag: '-a', desc: 'ローカルとリモートトラッキングブランチを両方表示' },
{ flag: '-r', desc: 'リモートトラッキングブランチのみ表示' },
{ flag: '-v', desc: '各ブランチの最新コミットも表示' },
],
variants: [
{ cmd: 'git branch -vv', desc: 'アップストリームのトラッキング情報も含めて表示' },
]
},
/* ── 取消・修正 ── */
{
id: 'reset-soft', cat: 'undo',
label: '直前のコミットを取消す（変更は保持）',
desc: 'HEAD を1コミット前に戻しつつ、変更内容はステージング状態で保持します。早まってコミットしたときに便利です。',
cmd: 'git reset --soft HEAD~1',
cmdDisplay: '<span class="git-keyword">git</span> reset <span class="git-flag">--soft</span> HEAD~1',
flags: [
{ flag: '--soft', desc: 'HEAD のみ移動。インデックスと作業ツリーは変更しない' },
{ flag: 'HEAD~1', desc: '現在の HEAD の1つ前のコミットを指定' },
],
variants: [
{ cmd: 'git reset --mixed HEAD~1', desc: 'ステージングも解除するが、ファイル自体は残す（デフォルト動作）' },
{ cmd: 'git reset --hard HEAD~1', desc: 'コミットと変更内容を完全に削除（破壊的）' },
]
},
{
id: 'revert', cat: 'undo',
label: 'コミットを安全に取り消す（revert）',
desc: '過去のコミットを打ち消す新しいコミットを作成します。履歴を書き換えないため、共有ブランチに安全です。',
cmd: 'git revert <コミットハッシュ>',
cmdDisplay: '<span class="git-keyword">git</span> revert <span class="git-placeholder">&lt;コミットハッシュ&gt;</span>',
flags: [],
variants: [
{ cmd: 'git revert HEAD', desc: '直前のコミットを revert する' },
{ cmd: 'git revert --no-commit HEAD~3..HEAD', desc: '直近3コミットを1つの revert コミットにまとめる' },
]
},
{
id: 'stash', cat: 'undo',
label: '変更を一時退避する（stash）',
desc: '未コミットの変更を一時的に棚上げして作業コンテキストを切り替え、後で復元できます。',
cmd: 'git stash',
cmdDisplay: '<span class="git-keyword">git</span> stash',
flags: [],
variants: [
{ cmd: 'git stash push -m "説明"', desc: '説明付きで stash する' },
{ cmd: 'git stash pop', desc: '最新の stash を適用してリストから削除する' },
{ cmd: 'git stash apply stash@{2}', desc: '特定の stash を適用するがリストには残す' },
{ cmd: 'git stash list', desc: 'すべての stash を一覧表示' },
{ cmd: 'git stash drop stash@{0}', desc: '特定の stash エントリを削除する' },
]
},
{
id: 'restore', cat: 'undo',
label: 'ファイルの変更を破棄する',
desc: '特定ファイルの未ステージの変更を破棄し、最後のコミット状態に戻します。',
cmd: 'git restore <ファイル名>',
cmdDisplay: '<span class="git-keyword">git</span> restore <span class="git-placeholder">&lt;ファイル名&gt;</span>',
flags: [],
variants: [
{ cmd: 'git restore --staged <ファイル名>', desc: 'ファイルをインデックスから取り除く（編集内容は保持）' },
{ cmd: 'git restore .', desc: 'カレントディレクトリの未ステージ変更をすべて破棄' },
{ cmd: 'git checkout -- <ファイル名>', desc: '従来の構文による同等操作' },
]
},
{
id: 'amend', cat: 'undo',
label: '直前のコミットメッセージを修正する',
desc: '最新コミットのメッセージを書き直します。共有ブランチにプッシュ済みの場合は使用しないでください。',
cmd: 'git commit --amend -m "修正したメッセージ"',
cmdDisplay: '<span class="git-keyword">git</span> commit <span class="git-flag">--amend</span> <span class="git-flag">-m</span> <span class="git-placeholder">"修正したメッセージ"</span>',
flags: [
{ flag: '--amend', desc: '直前のコミットを新しいコミットで置き換える（ツリーは同一）' },
{ flag: '-m', desc: '新しいコミットメッセージをインラインで指定' },
],
variants: [
{ cmd: 'git commit --amend --no-edit', desc: 'メッセージを変えずにステージ済みの変更を直前コミットへ追加' },
]
},
/* ── リモート ── */
{
id: 'remote-add', cat: 'remote',
label: 'リモートを追加する',
desc: 'ローカルリポジトリをリモートサーバー（GitHub・GitLab など）に接続します。',
cmd: 'git remote add origin <URL>',
cmdDisplay: '<span class="git-keyword">git</span> remote add origin <span class="git-placeholder">&lt;URL&gt;</span>',
flags: [],
variants: [
{ cmd: 'git remote -v', desc: '全リモートとその URL を一覧表示' },
{ cmd: 'git remote set-url origin <新URL>', desc: '既存リモートの URL を変更する' },
{ cmd: 'git remote remove <名前>', desc: 'リモートの接続を削除する' },
]
},
{
id: 'fetch', cat: 'remote',
label: 'リモートからフェッチする',
desc: 'リモートのオブジェクトと参照をダウンロードします。現在のブランチにはマージされません。',
cmd: 'git fetch origin',
cmdDisplay: '<span class="git-keyword">git</span> fetch origin',
flags: [],
variants: [
{ cmd: 'git fetch --all', desc: '設定されている全リモートからフェッチする' },
{ cmd: 'git fetch --prune', desc: 'リモートで削除されたブランチのトラッキング参照を削除する' },
]
},
{
id: 'pull', cat: 'remote',
label: 'リモートの変更をプルする',
desc: 'リモートトラッキングブランチの変更をフェッチして現在のブランチに統合します。',
cmd: 'git pull origin <ブランチ名>',
cmdDisplay: '<span class="git-keyword">git</span> pull origin <span class="git-placeholder">&lt;ブランチ名&gt;</span>',
flags: [],
variants: [
{ cmd: 'git pull --rebase origin <ブランチ名>', desc: 'マージの代わりにリベースで取り込む' },
{ cmd: 'git pull --ff-only', desc: 'fast-forward が可能な場合のみ更新する（分岐があると失敗）' },
]
},
{
id: 'push', cat: 'remote',
label: 'リモートにプッシュする',
desc: 'ローカルブランチのコミットをリモートリポジトリにアップロードします。',
cmd: 'git push origin <ブランチ名>',
cmdDisplay: '<span class="git-keyword">git</span> push origin <span class="git-placeholder">&lt;ブランチ名&gt;</span>',
flags: [],
variants: [
{ cmd: 'git push -u origin <ブランチ名>', desc: 'プッシュしてアップストリームを設定する（初回のみ）' },
{ cmd: 'git push --force-with-lease', desc: 'リモートに未取得のコミットがあれば中止する安全な強制プッシュ' },
{ cmd: 'git push --tags', desc: 'ローカルの全タグをリモートにプッシュする' },
]
},
/* ── 応用 ── */
{
id: 'rebase', cat: 'advanced',
label: '別のブランチにリベースする',
desc: '自分のブランチのコミットを別のブランチの先頭に移動・再適用し、直線的な履歴を作ります。',
cmd: 'git rebase <ベースブランチ>',
cmdDisplay: '<span class="git-keyword">git</span> rebase <span class="git-placeholder">&lt;ベースブランチ&gt;</span>',
flags: [],
variants: [
{ cmd: 'git rebase -i HEAD~3', desc: 'インタラクティブリベース: 直近3コミットをスカッシュ・並べ替え・編集' },
{ cmd: 'git rebase --continue', desc: 'コンフリクト解消後にリベースを再開する' },
{ cmd: 'git rebase --abort', desc: 'リベースを中断してリベース前の状態に戻す' },
]
},
{
id: 'cherry-pick', cat: 'advanced',
label: '特定のコミットだけを適用する（cherry-pick）',
desc: 'ブランチ全体をマージせずに、特定のコミットが加えた変更だけを現在のブランチに適用します。',
cmd: 'git cherry-pick <コミットハッシュ>',
cmdDisplay: '<span class="git-keyword">git</span> cherry-pick <span class="git-placeholder">&lt;コミットハッシュ&gt;</span>',
flags: [],
variants: [
{ cmd: 'git cherry-pick <hash1>..<hash2>', desc: '範囲指定で複数のコミットを適用する' },
{ cmd: 'git cherry-pick -n <hash>', desc: 'コミットを作らずに変更だけをステージングする' },
{ cmd: 'git cherry-pick --abort', desc: '進行中の cherry-pick をキャンセルする' },
]
},
{
id: 'bisect', cat: 'advanced',
label: 'バグ混入コミットを二分探索で見つける',
desc: 'バイナリサーチを使ってバグを導入したコミットを特定します。Git が中間点をチェックアウトするので、良い・悪いを回答するだけで原因を絞り込めます。',
cmd: 'git bisect start && git bisect bad && git bisect good <正常だったハッシュ>',
cmdDisplay: '<span class="git-keyword">git</span> bisect start\n<span class="git-keyword">git</span> bisect bad\n<span class="git-keyword">git</span> bisect good <span class="git-placeholder">&lt;正常だったハッシュ&gt;</span>',
flags: [],
variants: [
{ cmd: 'git bisect reset', desc: 'bisect セッションを終了し、元のブランチへ戻る' },
{ cmd: 'git bisect run <テストスクリプト>', desc: 'スクリプトで自動化: 正常なら 0、バグありなら非ゼロを返す' },
]
},
{
id: 'submodule', cat: 'advanced',
label: 'サブモジュールを追加する',
desc: '別の Git リポジトリをプロジェクトのサブディレクトリとして埋め込み、特定のコミットで追跡します。',
cmd: 'git submodule add <URL> <パス>',
cmdDisplay: '<span class="git-keyword">git</span> submodule add <span class="git-placeholder">&lt;URL&gt;</span> <span class="git-placeholder">&lt;パス&gt;</span>',
flags: [],
variants: [
{ cmd: 'git submodule update --init --recursive', desc: 'クローン後にすべてのサブモジュールを初期化・取得する' },
{ cmd: 'git submodule foreach git pull origin main', desc: 'すべてのサブモジュールで最新の変更を取得する' },
]
},
{
id: 'tag', cat: 'advanced',
label: 'バージョンタグを作成する',
desc: 'リリースバージョンとして特定のコミットにタグを付けます。注釈付きタグにはメッセージが含まれ、リリースに推奨されます。',
cmd: 'git tag -a v1.0.0 -m "Release v1.0.0"',
cmdDisplay: '<span class="git-keyword">git</span> tag <span class="git-flag">-a</span> <span class="git-placeholder">v1.0.0</span> <span class="git-flag">-m</span> <span class="git-placeholder">"Release v1.0.0"</span>',
flags: [
{ flag: '-a', desc: '注釈付きタグを作成（作成者・日時・メッセージを記録）' },
{ flag: '-m', desc: 'タグのメッセージをインラインで指定' },
],
variants: [
{ cmd: 'git tag', desc: '全タグを一覧表示する' },
{ cmd: 'git push origin --tags', desc: 'ローカルの全タグをリモートにプッシュする' },
{ cmd: 'git tag -d v1.0.0', desc: 'ローカルタグを削除する' },
]
},
];

var WORKFLOWS = [
{
title: '直前のコミットメッセージを修正する',
desc: 'タイポや曖昧なメッセージに気づいた。まだプッシュしていない場合。',
cmd: 'git commit --amend -m "正しいメッセージ"',
},
{
title: '直前のコミットを取り消す（ファイルは保持）',
desc: '早まってコミットした。変更をステージング状態に戻したい。',
cmd: 'git reset --soft HEAD~1',
},
{
title: 'フィーチャーブランチを作成する',
desc: 'main から分岐して新機能の開発を始める。',
cmd: 'git checkout -b feature/my-feature\n# ... 作業 ...\ngit push -u origin feature/my-feature',
},
{
title: '直近の N コミットをまとめる（スカッシュ）',
desc: '細かいコミットをマージ前に1つにまとめてきれいな履歴にする。',
cmd: 'git rebase -i HEAD~3\n# エディタで統合したいコミットの "pick" を "squash" に変更',
},
{
title: 'マージコンフリクトを解消する',
desc: 'コンフリクトが発生したファイルを編集し、解消済みとしてマークしてコミット。',
cmd: '# コンフリクトマーカーを編集して解消\ngit add <解消済みファイル>\ngit commit',
},
];

/* ── 状態 ────────────────────────────────────────────────────── */
var currentCat = 'all';
var currentScenario = null;
var searchQuery = '';

/* ── ユーティリティ ──────────────────────────────────────────── */
function $(id) { return document.getElementById(id); }

function filteredScenarios() {
var q = searchQuery.toLowerCase().trim();
return SCENARIOS.filter(function (s) {
var matchCat = currentCat === 'all' || s.cat === currentCat;
var matchQ = !q ||
s.label.toLowerCase().includes(q) ||
s.desc.toLowerCase().includes(q) ||
s.cmd.toLowerCase().includes(q) ||
s.cat.toLowerCase().includes(q);
return matchCat && matchQ;
});
}

function copyText(text, btn) {
navigator.clipboard.writeText(text).then(function () {
var orig = btn.textContent;
btn.textContent = 'コピー完了!';
btn.classList.add('copied');
setTimeout(function () {
btn.textContent = orig;
btn.classList.remove('copied');
}, 1800);
}).catch(function () {
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
var orig = btn.textContent;
btn.textContent = 'コピー完了!';
btn.classList.add('copied');
setTimeout(function () { btn.textContent = orig; btn.classList.remove('copied'); }, 1800);
});
}

/* ── タブ描画 ────────────────────────────────────────────────── */
function renderTabs() {
var container = $('git-tabs');
container.innerHTML = '';
CATEGORIES.forEach(function (cat) {
var btn = document.createElement('button');
btn.className = 'git-tab' + (cat.id === currentCat ? ' active' : '');
btn.textContent = cat.label;
btn.addEventListener('click', function () {
currentCat = cat.id;
searchQuery = '';
$('git-search').value = '';
renderAll();
});
container.appendChild(btn);
});
}

/* ── サイドバー描画 ──────────────────────────────────────────── */
function renderSidebar() {
var list = $('git-scenario-list');
var items = filteredScenarios();
list.innerHTML = '';

if (items.length === 0) {
var empty = document.createElement('div');
empty.className = 'git-no-results';
empty.textContent = '該当するシナリオが見つかりませんでした。';
list.appendChild(empty);
return;
}

var countEl = $('git-search-count');
if (searchQuery) {
countEl.textContent = '"' + searchQuery + '" の検索結果: ' + items.length + ' 件';
} else {
countEl.textContent = '';
}

items.forEach(function (s) {
var el = document.createElement('div');
el.className = 'git-scenario-item' + (currentScenario && currentScenario.id === s.id ? ' active' : '');
var catObj = CATEGORIES.find(function(c){ return c.id === s.cat; });
el.innerHTML = s.label + '<span class="git-badge">' + catObj.label + '</span>';
el.addEventListener('click', function () {
currentScenario = s;
renderSidebar();
renderOutput();
});
list.appendChild(el);
});
}

/* ── 出力パネル描画 ──────────────────────────────────────────── */
function renderOutput() {
var panel = $('git-output');
if (!currentScenario) {
panel.innerHTML = '<div class="git-placeholder-state"><div class="git-icon-big">&#9881;</div><p>左のパネルからシナリオを選ぶと、コマンドと解説が表示されます。</p></div>';
return;
}
var s = currentScenario;
var catLabel = CATEGORIES.find(function(c){ return c.id === s.cat; }).label;

var flagsHtml = '';
if (s.flags && s.flags.length > 0) {
var rows = s.flags.map(function (f) {
return '<tr><td><code>' + f.flag + '</code></td><td>' + f.desc + '</td></tr>';
}).join('');
flagsHtml = '<div class="git-flags-title">フラグ・引数の解説</div>' +
'<table class="git-flags-table"><thead><tr><th>フラグ / 引数</th><th>説明</th></tr></thead><tbody>' +
rows + '</tbody></table>';
}

var variantsHtml = '';
if (s.variants && s.variants.length > 0) {
var vitems = s.variants.map(function (v) {
return '<div class="git-variant-item"><span class="git-variant-cmd">' + v.cmd + '</span><span class="git-variant-desc">' + v.desc + '</span></div>';
}).join('');
variantsHtml = '<div class="git-variants"><div class="git-variants-title">バリエーション・関連コマンド</div>' + vitems + '</div>';
}

panel.innerHTML =
'<div class="git-output-header">' +
'<span class="git-output-title">' + s.label + '</span>' +
'<span class="git-cat-label">' + catLabel + '</span>' +
'</div>' +
'<div class="git-output-body">' +
'<div class="git-desc">' + s.desc + '</div>' +
'<div class="git-cmd-block">' +
'<div class="git-cmd-topbar">' +
'<span class="git-cmd-label">bash</span>' +
'<button class="git-copy-btn" id="git-main-copy">コピー</button>' +
'</div>' +
'<div class="git-cmd-code">' + s.cmdDisplay + '</div>' +
'</div>' +
flagsHtml +
variantsHtml +
'</div>';

document.getElementById('git-main-copy').addEventListener('click', function () {
copyText(s.cmd, this);
});
}

/* ── ワークフロー描画 ────────────────────────────────────────── */
function renderWorkflows() {
var grid = $('git-workflow-grid');
grid.innerHTML = '';
WORKFLOWS.forEach(function (w, idx) {
var card = document.createElement('div');
card.className = 'git-workflow-card';
card.innerHTML =
'<h4>' + w.title + '</h4>' +
'<p>' + w.desc + '</p>' +
'<code class="git-workflow-cmd">' + w.cmd + '</code>' +
'<div class="git-workflow-footer"><button class="git-workflow-copy" id="wf-copy-' + idx + '">コピー</button></div>';
grid.appendChild(card);
});
WORKFLOWS.forEach(function (w, idx) {
document.getElementById('wf-copy-' + idx).addEventListener('click', function () {
copyText(w.cmd, this);
});
});
}

/* ── 全体描画 ────────────────────────────────────────────────── */
function renderAll() {
renderTabs();
renderSidebar();
renderOutput();
}

/* ── 検索 ────────────────────────────────────────────────────── */
$('git-search').addEventListener('input', function () {
searchQuery = this.value;
currentCat = 'all';
currentScenario = null;
renderAll();
});

/* ── 初期化 ──────────────────────────────────────────────────── */
renderAll();
renderWorkflows();

})();
</script>

</div>

---

### 関連ツール

> cron 式を作成 → [Cron式ジェネレーター](/ja/tools/cron-generator/)
> 変更履歴を生成 → [変更履歴ジェネレーター](/ja/tools/changelog-generator/)
> .htaccess を作成 → [.htaccessジェネレーター](/ja/tools/htaccess-generator/)
