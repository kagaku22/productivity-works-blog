---
title: "GitHubプロフィールREADMEジェネレーター"
slug: "github-readme-generator"
date: 2025-04-12
description: "無料のGitHubプロフィールREADME作成ツール。自己紹介・スキル・統計・SNSリンクを設定してMarkdownを即生成。コピペで完了。"
categories: ["無料ツール"]
tags: ["github", "readme", "markdown", "開発者", "プロフィール"]
cover:
  image: "/images/covers/github-readme-generator-ja.png"
  alt: "GitHubプロフィールREADMEジェネレーター"
ShowToc: false
---

テンプレートを選んで入力するだけ。GitHubプロフィールに貼り付けられるREADMEのMarkdownを即座に生成します。

**関連ツール:** [マークダウンプレビュー](/ja/tools/markdown-preview/) &bull; [Gitコマンドジェネレーター](/ja/tools/git-command-generator/)

---

<div id="gh-app">

<style>
/* ── Reset & base ── */
#gh-app *{box-sizing:border-box;margin:0;padding:0}
#gh-app{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI","Hiragino Sans",Meiryo,sans-serif;color:#24292f;--accent:#0969da;--border:#d0d7de;--bg:#f6f8fa;--radius:6px;--pad:16px}

/* ── Layout ── */
#gh-app .gh-wrap{display:grid;grid-template-columns:1fr 1fr;gap:24px;margin-top:16px}
@media(max-width:820px){#gh-app .gh-wrap{grid-template-columns:1fr}}

/* ── Panels ── */
#gh-app .gh-panel{background:#fff;border:1px solid var(--border);border-radius:var(--radius);padding:var(--pad)}
#gh-app h2.gh-title{font-size:1rem;font-weight:600;margin-bottom:12px;display:flex;align-items:center;gap:6px}
#gh-app h2.gh-title svg{flex-shrink:0}

/* ── Toolbar ── */
#gh-app .gh-toolbar{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:20px;align-items:center}
#gh-app .gh-preset-btn{padding:6px 14px;border:1px solid var(--border);background:#fff;border-radius:20px;cursor:pointer;font-size:.85rem;transition:all .15s}
#gh-app .gh-preset-btn.active,#gh-app .gh-preset-btn:hover{background:var(--accent);color:#fff;border-color:var(--accent)}

/* ── Form ── */
#gh-app .gh-field{margin-bottom:14px}
#gh-app .gh-field label{display:block;font-size:.82rem;font-weight:600;color:#57606a;margin-bottom:4px}
#gh-app .gh-field input,#gh-app .gh-field textarea,#gh-app .gh-field select{width:100%;padding:7px 10px;border:1px solid var(--border);border-radius:var(--radius);font-size:.9rem;font-family:inherit;background:#fff;transition:border .15s}
#gh-app .gh-field input:focus,#gh-app .gh-field textarea:focus,#gh-app .gh-field select:focus{outline:none;border-color:var(--accent);box-shadow:0 0 0 3px rgba(9,105,218,.15)}
#gh-app .gh-field textarea{resize:vertical;min-height:64px}

/* ── Skills ── */
#gh-app .gh-skills-grid{display:flex;flex-wrap:wrap;gap:6px;margin-top:4px}
#gh-app .gh-skill-tag{padding:4px 10px;border:1px solid var(--border);border-radius:20px;font-size:.78rem;cursor:pointer;user-select:none;transition:all .15s;background:#fff}
#gh-app .gh-skill-tag.selected{background:var(--accent);color:#fff;border-color:var(--accent)}

/* ── Header style ── */
#gh-app .gh-style-grid{display:flex;gap:8px;flex-wrap:wrap;margin-top:4px}
#gh-app .gh-style-opt{padding:5px 12px;border:1px solid var(--border);border-radius:var(--radius);cursor:pointer;font-size:.82rem;background:#fff;transition:all .15s}
#gh-app .gh-style-opt.active{background:var(--accent);color:#fff;border-color:var(--accent)}

/* ── Checkboxes ── */
#gh-app .gh-checks{display:flex;flex-direction:column;gap:8px;margin-top:4px}
#gh-app .gh-check-row{display:flex;align-items:center;gap:8px;font-size:.88rem;cursor:pointer}
#gh-app .gh-check-row input[type=checkbox]{width:16px;height:16px;accent-color:var(--accent);cursor:pointer}

/* ── Preview ── */
#gh-app .gh-preview{background:var(--bg);border:1px solid var(--border);border-radius:var(--radius);padding:var(--pad);font-family:"SFMono-Regular",Consolas,monospace;font-size:.78rem;line-height:1.6;white-space:pre-wrap;word-break:break-all;max-height:620px;overflow-y:auto;color:#1f2328}

/* ── Copy button ── */
#gh-app .gh-copy-wrap{margin-top:10px;display:flex;gap:8px;align-items:center}
#gh-app .gh-copy-btn{padding:9px 20px;background:var(--accent);color:#fff;border:none;border-radius:var(--radius);cursor:pointer;font-size:.9rem;font-weight:600;transition:background .15s;flex:1}
#gh-app .gh-copy-btn:hover{background:#0757ba}
#gh-app .gh-copy-msg{font-size:.82rem;color:#1a7f37;display:none;align-items:center;gap:4px;font-weight:600}
#gh-app .gh-copy-msg.show{display:flex}
</style>

<!-- Toolbar -->
<div class="gh-toolbar">
  <span style="font-size:.85rem;font-weight:600;color:#57606a">テンプレート:</span>
  <button class="gh-preset-btn" onclick="ghApplyPreset('minimal')">シンプル</button>
  <button class="gh-preset-btn active" onclick="ghApplyPreset('developer')">開発者</button>
  <button class="gh-preset-btn" onclick="ghApplyPreset('creative')">クリエイティブ</button>
</div>

<div class="gh-wrap">

<!-- LEFT: Form -->
<div>

  <!-- Identity -->
  <div class="gh-panel" style="margin-bottom:16px">
    <h2 class="gh-title">
      <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><circle cx="8" cy="5" r="3" stroke="#57606a" stroke-width="1.5"/><path d="M2 14c0-3.314 2.686-6 6-6s6 2.686 6 6" stroke="#57606a" stroke-width="1.5" stroke-linecap="round"/></svg>
      プロフィール基本情報
    </h2>
    <div class="gh-field"><label>名前</label><input id="gh-name" type="text" placeholder="山田 太郎" oninput="ghGenerate()"></div>
    <div class="gh-field"><label>肩書き / 役割</label><input id="gh-title-input" type="text" placeholder="フルスタックエンジニア | OSS貢献者" oninput="ghGenerate()"></div>
    <div class="gh-field"><label>GitHubユーザー名（統計カード用）</label><input id="gh-user" type="text" placeholder="yamada-taro" oninput="ghGenerate()"></div>
    <div class="gh-field">
      <label>ヘッダースタイル</label>
      <div class="gh-style-grid">
        <div class="gh-style-opt active" data-style="wave" onclick="ghSetStyle('wave')">ウェーブ</div>
        <div class="gh-style-opt" data-style="gradient" onclick="ghSetStyle('gradient')">グラデーション</div>
        <div class="gh-style-opt" data-style="typing" onclick="ghSetStyle('typing')">タイピング</div>
        <div class="gh-style-opt" data-style="plain" onclick="ghSetStyle('plain')">シンプル</div>
      </div>
    </div>
  </div>

  <!-- About -->
  <div class="gh-panel" style="margin-bottom:16px">
    <h2 class="gh-title">
      <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><rect x="2" y="2" width="12" height="12" rx="2" stroke="#57606a" stroke-width="1.5"/><path d="M5 8h6M5 5.5h6M5 10.5h4" stroke="#57606a" stroke-width="1.5" stroke-linecap="round"/></svg>
      自己紹介
    </h2>
    <div class="gh-field"><label>自己紹介文</label><textarea id="gh-bio" placeholder="Webアプリ開発が好きなエンジニアです。OSSへの貢献も積極的に行っています。" oninput="ghGenerate()"></textarea></div>
    <div class="gh-field"><label>現在取り組んでいること</label><input id="gh-working" type="text" placeholder="オープンソースのCLIツール開発" oninput="ghGenerate()"></div>
    <div class="gh-field"><label>現在学んでいること</label><input id="gh-learning" type="text" placeholder="Rust、WebAssembly、GraphQL" oninput="ghGenerate()"></div>
    <div class="gh-field"><label>ちょっとした豆知識</label><input id="gh-fun" type="text" placeholder="コーヒーなしではコードが書けません" oninput="ghGenerate()"></div>
  </div>

  <!-- Skills -->
  <div class="gh-panel" style="margin-bottom:16px">
    <h2 class="gh-title">
      <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M5 4L2 8l3 4M11 4l3 4-3 4M8 2l-1.5 12" stroke="#57606a" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
      スキル・技術スタック
    </h2>
    <p style="font-size:.8rem;color:#57606a;margin-bottom:8px">使用している技術をクリックして選択</p>
    <div class="gh-skills-grid" id="gh-skills-grid"></div>
  </div>

  <!-- Social -->
  <div class="gh-panel" style="margin-bottom:16px">
    <h2 class="gh-title">
      <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><circle cx="12" cy="4" r="2" stroke="#57606a" stroke-width="1.5"/><circle cx="4" cy="8" r="2" stroke="#57606a" stroke-width="1.5"/><circle cx="12" cy="12" r="2" stroke="#57606a" stroke-width="1.5"/><path d="M6 7l4-2M6 9l4 2" stroke="#57606a" stroke-width="1.5" stroke-linecap="round"/></svg>
      SNS・連絡先
    </h2>
    <div class="gh-field"><label>GitHub URL</label><input id="gh-social-github" type="text" placeholder="https://github.com/yamada-taro" oninput="ghGenerate()"></div>
    <div class="gh-field"><label>Twitter / X URL</label><input id="gh-social-twitter" type="text" placeholder="https://twitter.com/yamada_taro" oninput="ghGenerate()"></div>
    <div class="gh-field"><label>LinkedIn URL</label><input id="gh-social-linkedin" type="text" placeholder="https://linkedin.com/in/yamada-taro" oninput="ghGenerate()"></div>
    <div class="gh-field"><label>Zenn URL</label><input id="gh-social-zenn" type="text" placeholder="https://zenn.dev/yamada_taro" oninput="ghGenerate()"></div>
    <div class="gh-field"><label>個人サイト</label><input id="gh-social-web" type="text" placeholder="https://yamada-taro.dev" oninput="ghGenerate()"></div>
    <div class="gh-field"><label>メールアドレス</label><input id="gh-social-email" type="text" placeholder="taro@example.com" oninput="ghGenerate()"></div>
  </div>

  <!-- Stats -->
  <div class="gh-panel">
    <h2 class="gh-title">
      <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M2 12l3-4 3 2 3-5 3 3" stroke="#57606a" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
      GitHub統計カード
    </h2>
    <div class="gh-checks">
      <label class="gh-check-row"><input type="checkbox" id="gh-stat-main" checked onchange="ghGenerate()"> GitHubステータスカード</label>
      <label class="gh-check-row"><input type="checkbox" id="gh-stat-streak" checked onchange="ghGenerate()"> ストリーク統計</label>
      <label class="gh-check-row"><input type="checkbox" id="gh-stat-langs" checked onchange="ghGenerate()"> 使用言語カード</label>
    </div>
    <div class="gh-field" style="margin-top:12px">
      <label>カードテーマ</label>
      <select id="gh-stat-theme" onchange="ghGenerate()">
        <option value="default">デフォルト</option>
        <option value="dark">ダーク</option>
        <option value="radical">ラディカル</option>
        <option value="merko">Merko</option>
        <option value="gruvbox">Gruvbox</option>
        <option value="tokyonight">東京ナイト</option>
        <option value="onedark">One Dark</option>
        <option value="cobalt">コバルト</option>
        <option value="synthwave">シンスウェーブ</option>
        <option value="highcontrast">ハイコントラスト</option>
      </select>
    </div>
  </div>

</div>

<!-- RIGHT: Preview -->
<div>
  <div class="gh-panel" style="position:sticky;top:80px">
    <h2 class="gh-title">
      <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M1 4h14M1 8h10M1 12h12" stroke="#57606a" stroke-width="1.5" stroke-linecap="round"/></svg>
      生成されたREADME.md
    </h2>
    <pre class="gh-preview" id="gh-preview"><!-- generated --></pre>
    <div class="gh-copy-wrap">
      <button class="gh-copy-btn" onclick="ghCopy()">README.mdをコピー</button>
      <span class="gh-copy-msg" id="gh-copy-msg">コピー完了!</span>
    </div>
  </div>
</div>

</div><!-- .gh-wrap -->

<script>
(function(){
"use strict";

var SKILLS = [
  {id:"js",    label:"JavaScript", color:"F7DF1E", logo:"javascript",    logoColor:"black"},
  {id:"ts",    label:"TypeScript", color:"3178C6", logo:"typescript",     logoColor:"white"},
  {id:"py",    label:"Python",     color:"3776AB", logo:"python",         logoColor:"white"},
  {id:"go",    label:"Go",         color:"00ADD8", logo:"go",             logoColor:"white"},
  {id:"rust",  label:"Rust",       color:"000000", logo:"rust",           logoColor:"white"},
  {id:"java",  label:"Java",       color:"ED8B00", logo:"openjdk",        logoColor:"white"},
  {id:"cpp",   label:"C++",        color:"00599C", logo:"cplusplus",      logoColor:"white"},
  {id:"cs",    label:"C#",         color:"512BD4", logo:"csharp",         logoColor:"white"},
  {id:"rb",    label:"Ruby",       color:"CC342D", logo:"ruby",           logoColor:"white"},
  {id:"php",   label:"PHP",        color:"777BB4", logo:"php",            logoColor:"white"},
  {id:"swift", label:"Swift",      color:"FA7343", logo:"swift",          logoColor:"white"},
  {id:"kt",    label:"Kotlin",     color:"7F52FF", logo:"kotlin",         logoColor:"white"},
  {id:"react", label:"React",      color:"20232A", logo:"react",          logoColor:"61DAFB"},
  {id:"vue",   label:"Vue.js",     color:"4FC08D", logo:"vuedotjs",       logoColor:"white"},
  {id:"ng",    label:"Angular",    color:"DD0031", logo:"angular",        logoColor:"white"},
  {id:"svelte",label:"Svelte",     color:"FF3E00", logo:"svelte",         logoColor:"white"},
  {id:"next",  label:"Next.js",    color:"000000", logo:"nextdotjs",      logoColor:"white"},
  {id:"nuxt",  label:"Nuxt.js",    color:"00DC82", logo:"nuxtdotjs",      logoColor:"white"},
  {id:"node",  label:"Node.js",    color:"339933", logo:"nodedotjs",      logoColor:"white"},
  {id:"deno",  label:"Deno",       color:"000000", logo:"deno",           logoColor:"white"},
  {id:"express",label:"Express",   color:"000000", logo:"express",        logoColor:"white"},
  {id:"fastapi",label:"FastAPI",   color:"009688", logo:"fastapi",        logoColor:"white"},
  {id:"django",label:"Django",     color:"092E20", logo:"django",         logoColor:"white"},
  {id:"rails", label:"Rails",      color:"CC0000", logo:"rubyonrails",    logoColor:"white"},
  {id:"laravel",label:"Laravel",   color:"FF2D20", logo:"laravel",        logoColor:"white"},
  {id:"docker",label:"Docker",     color:"2496ED", logo:"docker",         logoColor:"white"},
  {id:"k8s",   label:"Kubernetes", color:"326CE5", logo:"kubernetes",     logoColor:"white"},
  {id:"aws",   label:"AWS",        color:"FF9900", logo:"amazonaws",      logoColor:"white"},
  {id:"gcp",   label:"GCP",        color:"4285F4", logo:"googlecloud",    logoColor:"white"},
  {id:"azure", label:"Azure",      color:"0078D4", logo:"microsoftazure", logoColor:"white"},
  {id:"git",   label:"Git",        color:"F05032", logo:"git",            logoColor:"white"},
  {id:"linux", label:"Linux",      color:"FCC624", logo:"linux",          logoColor:"black"},
  {id:"pg",    label:"PostgreSQL", color:"4169E1", logo:"postgresql",     logoColor:"white"},
  {id:"mysql", label:"MySQL",      color:"4479A1", logo:"mysql",          logoColor:"white"},
  {id:"mongo", label:"MongoDB",    color:"47A248", logo:"mongodb",        logoColor:"white"},
  {id:"redis", label:"Redis",      color:"DC382D", logo:"redis",          logoColor:"white"},
  {id:"graphql",label:"GraphQL",   color:"E10098", logo:"graphql",        logoColor:"white"},
  {id:"figma", label:"Figma",      color:"F24E1E", logo:"figma",          logoColor:"white"},
];

var selected = {js:true, ts:true, react:true, node:true, docker:true, git:true};
var headerStyle = "wave";

/* Build skill grid */
var grid = document.getElementById("gh-skills-grid");
SKILLS.forEach(function(s){
  var el = document.createElement("div");
  el.className = "gh-skill-tag" + (selected[s.id] ? " selected" : "");
  el.textContent = s.label;
  el.dataset.id = s.id;
  el.addEventListener("click", function(){
    selected[s.id] = !selected[s.id];
    el.classList.toggle("selected", selected[s.id]);
    ghGenerate();
  });
  grid.appendChild(el);
});

/* Header style */
window.ghSetStyle = function(style){
  headerStyle = style;
  document.querySelectorAll("#gh-app .gh-style-opt").forEach(function(el){
    el.classList.toggle("active", el.dataset.style === style);
  });
  ghGenerate();
};

/* Presets */
var PRESETS = {
  minimal: {
    name:"山田 太郎", titleInput:"ソフトウェアエンジニア", user:"yamada-taro",
    bio:"コードを書くことが好きです。",
    working:"", learning:"", fun:"",
    skills:{js:true, py:true, git:true, linux:true},
    statMain:true, statStreak:false, statLangs:false, theme:"default", headerStyle:"plain",
    github:"", twitter:"", linkedin:"", zenn:"", web:"", email:""
  },
  developer: {
    name:"山田 太郎", titleInput:"フルスタックエンジニア | OSS貢献者", user:"yamada-taro",
    bio:"Webアプリ開発が好きなエンジニアです。OSSへの貢献も積極的に行っています。",
    working:"オープンソースのCLIツール開発", learning:"Rust、WebAssembly", fun:"コーヒーなしではコードが書けません",
    skills:{js:true, ts:true, react:true, node:true, docker:true, git:true, pg:true, py:true},
    statMain:true, statStreak:true, statLangs:true, theme:"tokyonight", headerStyle:"wave",
    github:"", twitter:"", linkedin:"", zenn:"", web:"", email:""
  },
  creative: {
    name:"山田 太郎", titleInput:"クリエイティブエンジニア & デザイナー", user:"yamada-taro",
    bio:"デザインとエンジニアリングの交差点で美しいデジタル体験を作っています。",
    working:"デザインシステムライブラリ", learning:"Three.js、WebGL", fun:"深夜2時にリリースします",
    skills:{js:true, ts:true, react:true, svelte:true, figma:true, node:true, git:true},
    statMain:true, statStreak:true, statLangs:true, theme:"radical", headerStyle:"gradient",
    github:"", twitter:"", linkedin:"", zenn:"", web:"", email:""
  }
};

window.ghApplyPreset = function(name){
  var p = PRESETS[name];
  document.getElementById("gh-name").value = p.name;
  document.getElementById("gh-title-input").value = p.titleInput;
  document.getElementById("gh-user").value = p.user;
  document.getElementById("gh-bio").value = p.bio;
  document.getElementById("gh-working").value = p.working;
  document.getElementById("gh-learning").value = p.learning;
  document.getElementById("gh-fun").value = p.fun;
  document.getElementById("gh-stat-main").checked = p.statMain;
  document.getElementById("gh-stat-streak").checked = p.statStreak;
  document.getElementById("gh-stat-langs").checked = p.statLangs;
  document.getElementById("gh-stat-theme").value = p.theme;
  selected = Object.assign({}, p.skills);
  document.querySelectorAll("#gh-skills-grid .gh-skill-tag").forEach(function(el){
    el.classList.toggle("selected", !!selected[el.dataset.id]);
  });
  document.querySelectorAll("#gh-app .gh-preset-btn").forEach(function(el){
    var map = {"シンプル":"minimal","開発者":"developer","クリエイティブ":"creative"};
    el.classList.toggle("active", map[el.textContent] === name);
  });
  ghSetStyle(p.headerStyle);
  ghGenerate();
};

function skillBadge(s){
  return "![" + s.label + "](https://img.shields.io/badge/" + encodeURIComponent(s.label) + "-" + s.color + "?style=for-the-badge&logo=" + s.logo + "&logoColor=" + s.logoColor + ")";
}

function socialBadge(label, color, logo, url){
  if(!url) return "";
  return "[![" + label + "](https://img.shields.io/badge/" + label + "-" + color + "?style=for-the-badge&logo=" + logo + "&logoColor=white)](" + url + ")";
}

window.ghGenerate = function(){
  var name       = document.getElementById("gh-name").value.trim() || "山田 太郎";
  var title      = document.getElementById("gh-title-input").value.trim() || "エンジニア";
  var user       = document.getElementById("gh-user").value.trim() || "yourusername";
  var bio        = document.getElementById("gh-bio").value.trim();
  var working    = document.getElementById("gh-working").value.trim();
  var learning   = document.getElementById("gh-learning").value.trim();
  var fun        = document.getElementById("gh-fun").value.trim();
  var theme      = document.getElementById("gh-stat-theme").value;
  var statMain   = document.getElementById("gh-stat-main").checked;
  var statStreak = document.getElementById("gh-stat-streak").checked;
  var statLangs  = document.getElementById("gh-stat-langs").checked;

  var socialGithub  = document.getElementById("gh-social-github").value.trim();
  var socialTwitter = document.getElementById("gh-social-twitter").value.trim();
  var socialLinkedin= document.getElementById("gh-social-linkedin").value.trim();
  var socialZenn    = document.getElementById("gh-social-zenn").value.trim();
  var socialWeb     = document.getElementById("gh-social-web").value.trim();
  var socialEmail   = document.getElementById("gh-social-email").value.trim();

  var lines = [];

  /* Header */
  if(headerStyle === "wave"){
    lines.push('<p align="center">');
    lines.push('  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=200&section=header&text=' + encodeURIComponent(name) + '&fontSize=50&fontAlignY=35&desc=' + encodeURIComponent(title) + '&descAlignY=55&descAlign=50&animation=fadeIn" />');
    lines.push("</p>");
    lines.push("");
  } else if(headerStyle === "gradient"){
    lines.push('<p align="center">');
    lines.push('  <img src="https://capsule-render.vercel.app/api?type=rect&color=gradient&customColorList=0,2,2,5,30&height=120&section=header&text=' + encodeURIComponent(name) + '&fontSize=45&fontColor=fff&fontAlignY=50&desc=' + encodeURIComponent(title) + '&descAlignY=75&descAlign=50" />');
    lines.push("</p>");
    lines.push("");
  } else if(headerStyle === "typing"){
    lines.push('<p align="center">');
    lines.push('  <img src="https://readme-typing-svg.demolab.com?font=Noto+Sans+JP&weight=600&size=28&pause=1000&color=0969DA&center=true&vCenter=true&width=600&lines=' + encodeURIComponent(name) + ';' + encodeURIComponent(title) + '" alt="Typing SVG" />');
    lines.push("</p>");
    lines.push("");
  } else {
    lines.push("# こんにちは、" + name + "です " + String.fromCodePoint(0x1F44B));
    lines.push("### " + title);
    lines.push("");
  }

  /* Visitor badge */
  lines.push('<p align="center">');
  lines.push('  <img src="https://komarev.com/ghpvc/?username=' + user + '&label=Profile%20views&color=0e75b6&style=flat" alt="profile views" />');
  lines.push("</p>");
  lines.push("");

  /* Bio */
  if(bio){
    lines.push("## 自己紹介");
    lines.push("");
    lines.push(bio);
    lines.push("");
  }

  /* Bullets */
  var bullets = [];
  if(working)  bullets.push(String.fromCodePoint(0x1F52D) + " 現在 **" + working + "** に取り組んでいます");
  if(learning) bullets.push(String.fromCodePoint(0x1F331) + " 現在 **" + learning + "** を学習中です");
  if(fun)      bullets.push(String.fromCodePoint(0x26A1) + " 豆知識: **" + fun + "**");
  if(bullets.length){
    bullets.forEach(function(b){ lines.push("- " + b); });
    lines.push("");
  }

  /* Social */
  var badges = [
    socialBadge("GitHub",   "181717", "github",      socialGithub),
    socialBadge("Twitter",  "1DA1F2", "twitter",     socialTwitter),
    socialBadge("LinkedIn", "0A66C2", "linkedin",    socialLinkedin),
    socialBadge("Zenn",     "3EA8FF", "zenn",        socialZenn),
    socialBadge("Website",  "4285F4", "googlechrome",socialWeb),
    socialEmail ? "[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:" + socialEmail + ")" : ""
  ].filter(Boolean);
  if(badges.length){
    lines.push("## SNS・連絡先");
    lines.push("");
    lines.push(badges.join(" "));
    lines.push("");
  }

  /* Skills */
  var chosen = SKILLS.filter(function(s){ return selected[s.id]; });
  if(chosen.length){
    lines.push("## 技術スタック");
    lines.push("");
    lines.push(chosen.map(skillBadge).join(" "));
    lines.push("");
  }

  /* Stats */
  if(statMain || statStreak || statLangs){
    lines.push("## GitHub統計");
    lines.push("");
    if(statMain && statLangs){
      lines.push('<p align="center">');
      lines.push('  <img height="180em" src="https://github-readme-stats.vercel.app/api?username=' + user + '&show_icons=true&theme=' + theme + '&include_all_commits=true&count_private=true&locale=ja"/>');
      lines.push('  <img height="180em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=' + user + '&layout=compact&langs_count=8&theme=' + theme + '&locale=ja"/>');
      lines.push("</p>");
    } else {
      if(statMain){
        lines.push('<p align="center">');
        lines.push('  <img src="https://github-readme-stats.vercel.app/api?username=' + user + '&show_icons=true&theme=' + theme + '&include_all_commits=true&count_private=true&locale=ja" />');
        lines.push("</p>");
      }
      if(statLangs){
        lines.push('<p align="center">');
        lines.push('  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=' + user + '&layout=compact&langs_count=8&theme=' + theme + '&locale=ja" />');
        lines.push("</p>");
      }
    }
    if(statStreak){
      lines.push('<p align="center">');
      lines.push('  <img src="https://github-readme-streak-stats.herokuapp.com/?user=' + user + '&theme=' + theme + '&locale=ja" />');
      lines.push("</p>");
    }
    lines.push("");
  }

  /* Footer wave */
  if(headerStyle === "wave" || headerStyle === "gradient"){
    lines.push('<p align="center">');
    lines.push('  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=80&section=footer" />');
    lines.push("</p>");
  }

  document.getElementById("gh-preview").textContent = lines.join("\n");
};

window.ghCopy = function(){
  var text = document.getElementById("gh-preview").textContent;
  if(navigator.clipboard && navigator.clipboard.writeText){
    navigator.clipboard.writeText(text).then(function(){
      var msg = document.getElementById("gh-copy-msg");
      msg.classList.add("show");
      setTimeout(function(){ msg.classList.remove("show"); }, 2000);
    });
  } else {
    var ta = document.createElement("textarea");
    ta.value = text;
    ta.style.position = "fixed";
    ta.style.opacity = "0";
    document.body.appendChild(ta);
    ta.select();
    document.execCommand("copy");
    document.body.removeChild(ta);
    var msg = document.getElementById("gh-copy-msg");
    msg.classList.add("show");
    setTimeout(function(){ msg.classList.remove("show"); }, 2000);
  }
};

ghApplyPreset("developer");

})();
</script>

</div><!-- #gh-app -->

---

## 使い方

1. GitHubで自分のユーザー名と同じ名前のリポジトリを作成します（例: `github.com/yamada-taro/yamada-taro`）
2. `README.md` ファイルを追加して初期化します
3. 上で生成したMarkdownをそのまま貼り付けます
4. コミット＆プッシュするとプロフィールページに自動表示されます

> 統計カードは [github-readme-stats](https://github.com/anuraghazra/github-readme-stats) と [streak-stats](https://github.com/DenverCoder1/github-readme-streak-stats) からリアルタイムデータを取得します。APIキーは不要です。

**関連ツール:** [マークダウンプレビュー](/ja/tools/markdown-preview/) &bull; [Gitコマンドジェネレーター](/ja/tools/git-command-generator/)

---

## 会計・経費管理をもっとラクに

エンジニアとして副業・フリーランスで活動するなら、**freee会計**で確定申告・請求書・経費管理を自動化しましょう。

<p>
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7T0MB6+52NU+5YZ75" rel="nofollow noopener" target="_blank">
<img src="https://www20.a8.net/svt/bgt?aid=FREEE_AID&wid=001&eno=01&mid=s00000FREEE&mc=1" width="300" height="100" alt="freee会計" border="0" />
</a>
</p>

---

<small>※ 本ページのfreeeリンクはアフィリエイトリンクを含む場合があります（A8.net）。</small>

---

> **確定申告・会計をもっとラクに？** [freee会計](https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP) なら、フリーランスの経費管理もクラウドで簡単。まずは無料で試してみましょう。

