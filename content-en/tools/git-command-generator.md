---
title: "Git Command Generator — Quick Reference"
date: 2025-05-16
description: "Generate git commands by scenario. Search common workflows like undo commits, create branches, and resolve conflicts. Copy commands with one click."
categories: ["Free Tools"]
tags: ["Developer Tools", "Documentation", "Free Tools"]
slug: "git-command-generator"
ShowToc: false
aliases:
  - "/tools/git-command-generator/"
  - "/tools/git-command-generator/"
cover:
  image: "/images/covers/git-command-generator.png"
  alt: "Git Command Generator"
---

Select a scenario to get the exact git command — with flag explanations and a one-click copy. No account needed.

<div id="git-app">
<style>
#git-app *,
#git-app *::before,
#git-app *::after {
box-sizing: border-box;
}
#git-app {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
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
text-transform: uppercase;
letter-spacing: 0.05em;
}
#git-app .git-output-body {
padding: 18px;
}
#git-app .git-desc {
font-size: 0.92rem;
color: #4a5568;
margin-bottom: 16px;
line-height: 1.55;
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
text-transform: uppercase;
letter-spacing: 0.05em;
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
text-transform: uppercase;
letter-spacing: 0.05em;
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
line-height: 1.4;
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
line-height: 1.5;
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
line-height: 1.4;
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

/* CTA */
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
line-height: 1.5;
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

<!-- Search -->
<div class="git-search-wrap">
<input type="text" id="git-search" placeholder="Search scenarios... e.g. undo, branch, rebase" autocomplete="off" />
<div class="git-search-count" id="git-search-count"></div>
</div>

<!-- Category tabs -->
<div class="git-tabs" id="git-tabs"></div>

<!-- Layout -->
<div class="git-layout">
<div class="git-sidebar">
<div class="git-scenario-list" id="git-scenario-list"></div>
</div>
<div class="git-main">
<div class="git-output" id="git-output">
<div class="git-placeholder-state">
<div class="git-icon-big">&#9881;</div>
<p>Select a scenario from the left panel to see the git command and explanation.</p>
</div>
</div>
</div>
</div>

<!-- Common Workflows -->
<div class="git-workflows" id="git-workflows">
<div class="git-workflows-title">&#9889; Common Workflows</div>
<div class="git-workflow-grid" id="git-workflow-grid"></div>
</div>

<script>
(function () {
'use strict';

/* ── DATA ─────────────────────────────────────────────────────── */
var CATEGORIES = [
{ id: 'all',      label: 'All' },
{ id: 'basic',    label: 'Basic' },
{ id: 'branch',   label: 'Branching' },
{ id: 'undo',     label: 'Undoing' },
{ id: 'remote',   label: 'Remote' },
{ id: 'advanced', label: 'Advanced' },
];

var SCENARIOS = [
/* ── BASIC ── */
{
id: 'init', cat: 'basic',
label: 'Initialize repository',
desc: 'Create a new Git repository in the current directory. This creates a hidden .git folder that tracks all changes.',
cmd: 'git init',
cmdDisplay: '<span class="git-keyword">git</span> init',
flags: [],
variants: [
{ cmd: 'git init <directory>', desc: 'Initialize in a specific directory (creates it if needed)' },
{ cmd: 'git init --bare', desc: 'Create a bare repository (no working tree, used for remote servers)' },
]
},
{
id: 'clone', cat: 'basic',
label: 'Clone a repository',
desc: 'Download a repository from a remote URL and create a local copy with full history.',
cmd: 'git clone <url>',
cmdDisplay: '<span class="git-keyword">git</span> clone <span class="git-placeholder">&lt;url&gt;</span>',
flags: [],
variants: [
{ cmd: 'git clone <url> <directory>', desc: 'Clone into a specific directory name' },
{ cmd: 'git clone --depth 1 <url>', desc: 'Shallow clone — only the latest snapshot (faster for large repos)' },
{ cmd: 'git clone -b <branch> <url>', desc: 'Clone and checkout a specific branch' },
]
},
{
id: 'add-all', cat: 'basic',
label: 'Stage all changes',
desc: 'Add all modified and new files in the working directory to the staging area (index), ready for commit.',
cmd: 'git add .',
cmdDisplay: '<span class="git-keyword">git</span> add <span class="git-flag">.</span>',
flags: [
{ flag: '.', desc: 'Stage all changes in the current directory and subdirectories' },
],
variants: [
{ cmd: 'git add -A', desc: 'Stage all changes including deletions in the entire repo' },
{ cmd: 'git add <file>', desc: 'Stage a specific file only' },
{ cmd: 'git add -p', desc: 'Interactively choose which hunks to stage (patch mode)' },
]
},
{
id: 'commit', cat: 'basic',
label: 'Commit staged changes',
desc: 'Save staged changes to the repository history with a descriptive message.',
cmd: 'git commit -m "Your commit message"',
cmdDisplay: '<span class="git-keyword">git</span> commit <span class="git-flag">-m</span> <span class="git-placeholder">"Your commit message"</span>',
flags: [
{ flag: '-m "<message>"', desc: 'Specify the commit message inline' },
],
variants: [
{ cmd: 'git commit -am "message"', desc: 'Stage all tracked modified files and commit in one step' },
{ cmd: 'git commit --amend -m "new message"', desc: 'Replace the last commit message (do not use if already pushed)' },
{ cmd: 'git commit --no-edit --amend', desc: 'Amend last commit keeping the existing message' },
]
},
{
id: 'status', cat: 'basic',
label: 'Check working tree status',
desc: 'Show which files are staged, modified, or untracked in the current working directory.',
cmd: 'git status',
cmdDisplay: '<span class="git-keyword">git</span> status',
flags: [],
variants: [
{ cmd: 'git status -s', desc: 'Short / compact output format' },
{ cmd: 'git status --ignored', desc: 'Also show ignored files' },
]
},
{
id: 'log', cat: 'basic',
label: 'View commit history',
desc: 'List recent commits with author, date, and message.',
cmd: 'git log --oneline --graph --decorate',
cmdDisplay: '<span class="git-keyword">git</span> log <span class="git-flag">--oneline --graph --decorate</span>',
flags: [
{ flag: '--oneline', desc: 'Condense each commit to one line' },
{ flag: '--graph', desc: 'Draw an ASCII branch graph on the left' },
{ flag: '--decorate', desc: 'Show branch and tag names next to commits' },
],
variants: [
{ cmd: 'git log -n 10', desc: 'Show only the last 10 commits' },
{ cmd: 'git log --author="Name"', desc: 'Filter commits by author' },
{ cmd: 'git log --since="2 weeks ago"', desc: 'Show commits from the last 2 weeks' },
{ cmd: 'git log -- <file>', desc: 'Show commits that touched a specific file' },
]
},
{
id: 'diff', cat: 'basic',
label: 'Show unstaged changes',
desc: 'Display line-by-line differences between the working directory and the index (staged snapshot).',
cmd: 'git diff',
cmdDisplay: '<span class="git-keyword">git</span> diff',
flags: [],
variants: [
{ cmd: 'git diff --staged', desc: 'Show differences between staged changes and last commit' },
{ cmd: 'git diff HEAD', desc: 'All changes (staged + unstaged) compared to last commit' },
{ cmd: 'git diff <branch1>..<branch2>', desc: 'Compare two branches' },
]
},
/* ── BRANCHING ── */
{
id: 'branch-create', cat: 'branch',
label: 'Create a new branch',
desc: 'Create a new branch pointing to the current commit, then switch to it immediately.',
cmd: 'git checkout -b <branch-name>',
cmdDisplay: '<span class="git-keyword">git</span> checkout <span class="git-flag">-b</span> <span class="git-placeholder">&lt;branch-name&gt;</span>',
flags: [
{ flag: '-b', desc: 'Create the branch and switch to it in one step' },
],
variants: [
{ cmd: 'git switch -c <branch-name>', desc: 'Modern syntax (Git 2.23+): create and switch' },
{ cmd: 'git branch <branch-name>', desc: 'Create branch without switching to it' },
{ cmd: 'git checkout -b <branch> origin/<branch>', desc: 'Create a local branch tracking a remote branch' },
]
},
{
id: 'branch-switch', cat: 'branch',
label: 'Switch to a branch',
desc: 'Move HEAD to another existing branch, updating your working directory.',
cmd: 'git switch <branch-name>',
cmdDisplay: '<span class="git-keyword">git</span> switch <span class="git-placeholder">&lt;branch-name&gt;</span>',
flags: [],
variants: [
{ cmd: 'git checkout <branch-name>', desc: 'Classic syntax for switching branches' },
{ cmd: 'git switch -', desc: 'Switch back to the previously checked-out branch' },
]
},
{
id: 'branch-merge', cat: 'branch',
label: 'Merge a branch',
desc: 'Integrate changes from another branch into the current branch by creating a merge commit.',
cmd: 'git merge <branch-name>',
cmdDisplay: '<span class="git-keyword">git</span> merge <span class="git-placeholder">&lt;branch-name&gt;</span>',
flags: [],
variants: [
{ cmd: 'git merge --no-ff <branch>', desc: 'Force a merge commit even if fast-forward is possible' },
{ cmd: 'git merge --squash <branch>', desc: 'Squash all branch commits into one staged change (does not auto-commit)' },
{ cmd: 'git merge --abort', desc: 'Cancel an in-progress merge and return to pre-merge state' },
]
},
{
id: 'branch-delete', cat: 'branch',
label: 'Delete a branch',
desc: 'Remove a merged branch locally. Use -D to force-delete unmerged branches.',
cmd: 'git branch -d <branch-name>',
cmdDisplay: '<span class="git-keyword">git</span> branch <span class="git-flag">-d</span> <span class="git-placeholder">&lt;branch-name&gt;</span>',
flags: [
{ flag: '-d', desc: 'Delete the branch (safe — only works if fully merged)' },
{ flag: '-D', desc: 'Force delete even if not merged' },
],
variants: [
{ cmd: 'git push origin --delete <branch>', desc: 'Delete a remote branch' },
{ cmd: 'git branch -D <branch>', desc: 'Force-delete a local branch regardless of merge status' },
]
},
{
id: 'branch-list', cat: 'branch',
label: 'List all branches',
desc: 'Show all local and remote branches, with the current branch highlighted.',
cmd: 'git branch -a',
cmdDisplay: '<span class="git-keyword">git</span> branch <span class="git-flag">-a</span>',
flags: [
{ flag: '-a', desc: 'List both local and remote-tracking branches' },
{ flag: '-r', desc: 'List only remote-tracking branches' },
{ flag: '-v', desc: 'Show last commit on each branch' },
],
variants: [
{ cmd: 'git branch -vv', desc: 'Show branches with upstream tracking info' },
]
},
/* ── UNDOING ── */
{
id: 'reset-soft', cat: 'undo',
label: 'Undo last commit (keep changes)',
desc: 'Move HEAD back one commit but keep all your changes staged. Useful when you committed too early.',
cmd: 'git reset --soft HEAD~1',
cmdDisplay: '<span class="git-keyword">git</span> reset <span class="git-flag">--soft</span> HEAD~1',
flags: [
{ flag: '--soft', desc: 'Reset HEAD only; staged index and working directory are untouched' },
{ flag: 'HEAD~1', desc: 'Target one commit behind the current HEAD' },
],
variants: [
{ cmd: 'git reset --mixed HEAD~1', desc: 'Unstage changes too, but keep files in working directory (default)' },
{ cmd: 'git reset --hard HEAD~1', desc: 'Discard the commit AND all its changes permanently (destructive)' },
]
},
{
id: 'revert', cat: 'undo',
label: 'Revert a commit (safe undo)',
desc: 'Create a new commit that reverses a previous commit. Safe for shared branches because it does not rewrite history.',
cmd: 'git revert <commit-hash>',
cmdDisplay: '<span class="git-keyword">git</span> revert <span class="git-placeholder">&lt;commit-hash&gt;</span>',
flags: [],
variants: [
{ cmd: 'git revert HEAD', desc: 'Revert the very last commit' },
{ cmd: 'git revert --no-commit HEAD~3..HEAD', desc: 'Revert last 3 commits without creating 3 separate revert commits' },
]
},
{
id: 'stash', cat: 'undo',
label: 'Stash uncommitted changes',
desc: 'Temporarily shelve changes so you can switch context, then restore them later.',
cmd: 'git stash',
cmdDisplay: '<span class="git-keyword">git</span> stash',
flags: [],
variants: [
{ cmd: 'git stash push -m "description"', desc: 'Stash with a descriptive name' },
{ cmd: 'git stash pop', desc: 'Apply the most recent stash and remove it from the stash list' },
{ cmd: 'git stash apply stash@{2}', desc: 'Apply a specific stash without removing it' },
{ cmd: 'git stash list', desc: 'List all stashes' },
{ cmd: 'git stash drop stash@{0}', desc: 'Delete a specific stash entry' },
]
},
{
id: 'restore', cat: 'undo',
label: 'Discard changes in a file',
desc: 'Discard unstaged changes in a specific file, restoring it to the last committed state.',
cmd: 'git restore <file>',
cmdDisplay: '<span class="git-keyword">git</span> restore <span class="git-placeholder">&lt;file&gt;</span>',
flags: [],
variants: [
{ cmd: 'git restore --staged <file>', desc: 'Unstage a file (remove from index) without discarding edits' },
{ cmd: 'git restore .', desc: 'Discard all unstaged changes in the current directory' },
{ cmd: 'git checkout -- <file>', desc: 'Classic syntax equivalent' },
]
},
{
id: 'amend', cat: 'undo',
label: 'Fix last commit message',
desc: 'Update the message of the most recent commit. Only safe if the commit has not been pushed to a shared branch.',
cmd: 'git commit --amend -m "corrected message"',
cmdDisplay: '<span class="git-keyword">git</span> commit <span class="git-flag">--amend</span> <span class="git-flag">-m</span> <span class="git-placeholder">"corrected message"</span>',
flags: [
{ flag: '--amend', desc: 'Replace the last commit with a new one (same tree, new message)' },
{ flag: '-m', desc: 'Specify the new commit message inline' },
],
variants: [
{ cmd: 'git commit --amend --no-edit', desc: 'Add staged changes to last commit without changing the message' },
]
},
/* ── REMOTE ── */
{
id: 'remote-add', cat: 'remote',
label: 'Add a remote',
desc: 'Connect your local repository to a remote server (e.g. GitHub, GitLab).',
cmd: 'git remote add origin <url>',
cmdDisplay: '<span class="git-keyword">git</span> remote add origin <span class="git-placeholder">&lt;url&gt;</span>',
flags: [],
variants: [
{ cmd: 'git remote -v', desc: 'List all remotes with their URLs' },
{ cmd: 'git remote set-url origin <new-url>', desc: 'Change the URL of an existing remote' },
{ cmd: 'git remote remove <name>', desc: 'Remove a remote connection' },
]
},
{
id: 'fetch', cat: 'remote',
label: 'Fetch from remote',
desc: 'Download objects and refs from a remote without merging them into your working branch.',
cmd: 'git fetch origin',
cmdDisplay: '<span class="git-keyword">git</span> fetch origin',
flags: [],
variants: [
{ cmd: 'git fetch --all', desc: 'Fetch from all configured remotes' },
{ cmd: 'git fetch --prune', desc: 'Remove remote-tracking branches that no longer exist on the remote' },
]
},
{
id: 'pull', cat: 'remote',
label: 'Pull changes from remote',
desc: 'Fetch and integrate changes from the remote tracking branch into the current branch.',
cmd: 'git pull origin <branch>',
cmdDisplay: '<span class="git-keyword">git</span> pull origin <span class="git-placeholder">&lt;branch&gt;</span>',
flags: [],
variants: [
{ cmd: 'git pull --rebase origin <branch>', desc: 'Rebase local commits on top of fetched commits instead of merging' },
{ cmd: 'git pull --ff-only', desc: 'Only update if fast-forward is possible (fails on divergence)' },
]
},
{
id: 'push', cat: 'remote',
label: 'Push to remote',
desc: 'Upload local branch commits to the remote repository.',
cmd: 'git push origin <branch>',
cmdDisplay: '<span class="git-keyword">git</span> push origin <span class="git-placeholder">&lt;branch&gt;</span>',
flags: [],
variants: [
{ cmd: 'git push -u origin <branch>', desc: 'Push and set the upstream tracking reference (use once)' },
{ cmd: 'git push --force-with-lease', desc: 'Force push but abort if the remote has new commits you have not seen (safer than --force)' },
{ cmd: 'git push --tags', desc: 'Push all local tags to the remote' },
]
},
/* ── ADVANCED ── */
{
id: 'rebase', cat: 'advanced',
label: 'Rebase onto another branch',
desc: 'Move or replay your branch commits on top of another branch, resulting in a linear history.',
cmd: 'git rebase <base-branch>',
cmdDisplay: '<span class="git-keyword">git</span> rebase <span class="git-placeholder">&lt;base-branch&gt;</span>',
flags: [],
variants: [
{ cmd: 'git rebase -i HEAD~3', desc: 'Interactive rebase: squash, reorder, or edit the last 3 commits' },
{ cmd: 'git rebase --continue', desc: 'Continue after resolving conflicts during a rebase' },
{ cmd: 'git rebase --abort', desc: 'Cancel the rebase and return to the pre-rebase state' },
]
},
{
id: 'cherry-pick', cat: 'advanced',
label: 'Cherry-pick a commit',
desc: 'Apply the changes introduced by a specific commit onto the current branch without merging the whole branch.',
cmd: 'git cherry-pick <commit-hash>',
cmdDisplay: '<span class="git-keyword">git</span> cherry-pick <span class="git-placeholder">&lt;commit-hash&gt;</span>',
flags: [],
variants: [
{ cmd: 'git cherry-pick <hash1>..<hash2>', desc: 'Apply a range of commits' },
{ cmd: 'git cherry-pick -n <hash>', desc: 'Apply changes without creating a commit (stage only)' },
{ cmd: 'git cherry-pick --abort', desc: 'Cancel an in-progress cherry-pick' },
]
},
{
id: 'bisect', cat: 'advanced',
label: 'Find a bug with bisect',
desc: 'Use binary search to find which commit introduced a bug. Git checks out midpoints until the culprit is found.',
cmd: 'git bisect start && git bisect bad && git bisect good <known-good-hash>',
cmdDisplay: '<span class="git-keyword">git</span> bisect start\n<span class="git-keyword">git</span> bisect bad\n<span class="git-keyword">git</span> bisect good <span class="git-placeholder">&lt;known-good-hash&gt;</span>',
flags: [],
variants: [
{ cmd: 'git bisect reset', desc: 'End the bisect session and return to original branch' },
{ cmd: 'git bisect run <test-script>', desc: 'Automate bisect with a script that exits 0 for good, non-zero for bad' },
]
},
{
id: 'submodule', cat: 'advanced',
label: 'Add a submodule',
desc: 'Embed another Git repository as a subdirectory of your project, tracked at a specific commit.',
cmd: 'git submodule add <url> <path>',
cmdDisplay: '<span class="git-keyword">git</span> submodule add <span class="git-placeholder">&lt;url&gt;</span> <span class="git-placeholder">&lt;path&gt;</span>',
flags: [],
variants: [
{ cmd: 'git submodule update --init --recursive', desc: 'Initialize and fetch all submodules after cloning' },
{ cmd: 'git submodule foreach git pull origin main', desc: 'Pull latest changes in all submodules' },
]
},
{
id: 'tag', cat: 'advanced',
label: 'Create a version tag',
desc: 'Mark a specific commit as a release version. Annotated tags include a message and are recommended for releases.',
cmd: 'git tag -a v1.0.0 -m "Release v1.0.0"',
cmdDisplay: '<span class="git-keyword">git</span> tag <span class="git-flag">-a</span> <span class="git-placeholder">v1.0.0</span> <span class="git-flag">-m</span> <span class="git-placeholder">"Release v1.0.0"</span>',
flags: [
{ flag: '-a', desc: 'Create an annotated tag (stores tagger name, date, and message)' },
{ flag: '-m', desc: 'Specify the tag message inline' },
],
variants: [
{ cmd: 'git tag', desc: 'List all tags' },
{ cmd: 'git push origin --tags', desc: 'Push all local tags to the remote' },
{ cmd: 'git tag -d v1.0.0', desc: 'Delete a local tag' },
]
},
];

var WORKFLOWS = [
{
title: 'Fix last commit message',
desc: 'You made a typo or wrote a vague commit message and have not pushed yet.',
cmd: 'git commit --amend -m "correct message here"',
},
{
title: 'Undo last commit (keep files)',
desc: 'Committed too early? Move the commit back to staged changes.',
cmd: 'git reset --soft HEAD~1',
},
{
title: 'Create a feature branch',
desc: 'Start work on a new feature isolated from main.',
cmd: 'git checkout -b feature/my-feature\n# ... do work ...\ngit push -u origin feature/my-feature',
},
{
title: 'Squash last N commits',
desc: 'Combine several small commits into one clean commit before merging.',
cmd: 'git rebase -i HEAD~3\n# In editor: change "pick" to "squash" for commits to merge',
},
{
title: 'Resolve merge conflicts',
desc: 'After a conflicted merge, edit files, then mark resolved and complete.',
cmd: '# Edit conflicted files to resolve markers\ngit add <resolved-file>\ngit commit',
},
];

/* ── STATE ─────────────────────────────────────────────────────── */
var currentCat = 'all';
var currentScenario = null;
var searchQuery = '';

/* ── HELPERS ───────────────────────────────────────────────────── */
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
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function () {
btn.textContent = orig;
btn.classList.remove('copied');
}, 1800);
}).catch(function () {
/* Fallback */
var ta = document.createElement('textarea');
ta.value = text;
ta.style.position = 'fixed';
ta.style.opacity = '0';
document.body.appendChild(ta);
ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
var orig = btn.textContent;
btn.textContent = 'Copied!';
btn.classList.add('copied');
setTimeout(function () { btn.textContent = orig; btn.classList.remove('copied'); }, 1800);
});
}

/* ── RENDER TABS ───────────────────────────────────────────────── */
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

/* ── RENDER SIDEBAR ────────────────────────────────────────────── */
function renderSidebar() {
var list = $('git-scenario-list');
var items = filteredScenarios();
list.innerHTML = '';

if (items.length === 0) {
var empty = document.createElement('div');
empty.className = 'git-no-results';
empty.textContent = 'No matching scenarios.';
list.appendChild(empty);
return;
}

var countEl = $('git-search-count');
if (searchQuery) {
countEl.textContent = items.length + ' result' + (items.length !== 1 ? 's' : '') + ' for "' + searchQuery + '"';
} else {
countEl.textContent = '';
}

items.forEach(function (s) {
var el = document.createElement('div');
el.className = 'git-scenario-item' + (currentScenario && currentScenario.id === s.id ? ' active' : '');
el.innerHTML = s.label +
'<span class="git-badge">' + CATEGORIES.find(function(c){ return c.id === s.cat; }).label + '</span>';
el.addEventListener('click', function () {
currentScenario = s;
renderSidebar();
renderOutput();
});
list.appendChild(el);
});
}

/* ── RENDER OUTPUT ─────────────────────────────────────────────── */
function renderOutput() {
var panel = $('git-output');
if (!currentScenario) {
panel.innerHTML = '<div class="git-placeholder-state"><div class="git-icon-big">&#9881;</div><p>Select a scenario from the left panel to see the git command and explanation.</p></div>';
return;
}
var s = currentScenario;
var catLabel = CATEGORIES.find(function(c){ return c.id === s.cat; }).label;

var flagsHtml = '';
if (s.flags && s.flags.length > 0) {
var rows = s.flags.map(function (f) {
return '<tr><td><code>' + f.flag + '</code></td><td>' + f.desc + '</td></tr>';
}).join('');
flagsHtml = '<div class="git-flags-title">Flag Reference</div>' +
'<table class="git-flags-table"><thead><tr><th>Flag / Argument</th><th>Description</th></tr></thead><tbody>' +
rows + '</tbody></table>';
}

var variantsHtml = '';
if (s.variants && s.variants.length > 0) {
var vitems = s.variants.map(function (v) {
return '<div class="git-variant-item"><span class="git-variant-cmd">' + v.cmd + '</span><span class="git-variant-desc">' + v.desc + '</span></div>';
}).join('');
variantsHtml = '<div class="git-variants"><div class="git-variants-title">Variants & Related Commands</div>' + vitems + '</div>';
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
'<button class="git-copy-btn" id="git-main-copy">Copy</button>' +
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

/* ── RENDER WORKFLOWS ──────────────────────────────────────────── */
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
'<div class="git-workflow-footer"><button class="git-workflow-copy" id="wf-copy-' + idx + '">Copy</button></div>';
grid.appendChild(card);
});
WORKFLOWS.forEach(function (w, idx) {
document.getElementById('wf-copy-' + idx).addEventListener('click', function () {
copyText(w.cmd, this);
});
});
}

/* ── RENDER ALL ────────────────────────────────────────────────── */
function renderAll() {
renderTabs();
renderSidebar();
renderOutput();
}

/* ── SEARCH ────────────────────────────────────────────────────── */
$('git-search').addEventListener('input', function () {
searchQuery = this.value;
currentCat = 'all';
currentScenario = null;
renderAll();
});

/* ── INIT ──────────────────────────────────────────────────────── */
renderAll();
renderWorkflows();

})();
</script>

</div>

---

### Related Tools

> Build cron expressions → [Cron Expression Generator](/tools/cron-generator/)
> Generate changelogs → [Changelog Generator](/tools/changelog-generator/)
> Build .htaccess → [.htaccess Generator](/tools/htaccess-generator/)
