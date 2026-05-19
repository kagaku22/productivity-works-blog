---
title: "絵文字検索＆コピーツール"
date: 2025-08-20
description: "無料の絵文字検索ツール。1500以上の絵文字をキーワードで検索。カテゴリ別一覧・ワンクリックコピー・Unicode/HTML表示対応。SNS投稿に最適。"
categories: ["無料ツール"]
tags: ["絵文字検索", "絵文字コピー", "emoji", "絵文字ツール", "無料ツール"]
slug: "emoji-search"
cover:
  image: "/images/covers/emoji-search-ja.png"
  alt: "絵文字検索＆コピーツール"
ShowToc: false
---

<div id="es-app">

<style>
#es-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', Roboto, sans-serif;
max-width: 960px;
margin: 0 auto;
padding: 0 0 40px 0;
color: #f1f5f9;
}
#es-app * { box-sizing: border-box; }

.es-hero {
background: linear-gradient(135deg, #1e3a5f 0%, #1e40af 50%, #1d4ed8 100%);
border-radius: 16px;
padding: 36px 32px;
margin-bottom: 24px;
text-align: center;
}
.es-hero h1 { font-size: 1.9rem; font-weight: 800; color: #bfdbfe; margin: 0 0 8px 0; }
.es-hero p  { color: #93c5fd; margin: 0; font-size: 1rem; }

.es-search-row {
display: flex;
gap: 10px;
align-items: center;
flex-wrap: wrap;
margin-bottom: 14px;
}
.es-search {
flex: 1;
min-width: 220px;
padding: 11px 16px;
border-radius: 10px;
border: 2px solid #3b82f6;
background: #1e293b;
color: #f1f5f9;
font-size: 1rem;
outline: none;
transition: border-color 0.2s;
}
.es-search::placeholder { color: #64748b; }
.es-search:focus { border-color: #60a5fa; }

.es-tone-wrap {
display: flex;
align-items: center;
gap: 6px;
flex-shrink: 0;
}
.es-tone-label { color: #93c5fd; font-size: 0.82rem; font-weight: 600; white-space: nowrap; }
.es-tone-buttons { display: flex; gap: 5px; }
.es-tone-btn {
width: 28px; height: 28px;
border-radius: 50%;
border: 2px solid transparent;
cursor: pointer;
font-size: 1rem;
display: flex; align-items: center; justify-content: center;
background: #1e293b;
transition: border-color 0.2s, transform 0.1s;
}
.es-tone-btn:hover { transform: scale(1.2); }
.es-tone-btn.active { border-color: #3b82f6; }

.es-tabs {
display: flex;
gap: 6px;
flex-wrap: wrap;
margin-bottom: 14px;
}
.es-tab {
padding: 6px 13px;
border-radius: 20px;
border: 2px solid #334155;
background: #1e293b;
color: #94a3b8;
cursor: pointer;
font-size: 0.82rem;
font-weight: 600;
transition: all 0.2s;
white-space: nowrap;
}
.es-tab:hover { border-color: #3b82f6; color: #93c5fd; }
.es-tab.active { background: #3b82f6; border-color: #3b82f6; color: #fff; }

.es-section-label {
font-size: 0.75rem;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.08em;
color: #3b82f6;
margin: 0 0 8px 0;
}

.es-recent-box {
background: #1e293b;
border-radius: 12px;
padding: 12px 14px;
margin-bottom: 14px;
border: 1px solid #334155;
}
.es-recent-row { display: flex; flex-wrap: wrap; gap: 3px; }

.es-grid-box {
background: #1e293b;
border-radius: 12px;
padding: 12px 14px;
border: 1px solid #334155;
margin-bottom: 14px;
}
.es-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(44px, 1fr));
gap: 3px;
}
.es-cell {
width: 44px; height: 44px;
display: flex; align-items: center; justify-content: center;
font-size: 1.5rem;
border-radius: 8px;
cursor: pointer;
transition: background 0.15s, transform 0.1s;
position: relative;
border: 2px solid transparent;
}
.es-cell:hover { background: #334155; transform: scale(1.18); z-index: 2; }
.es-cell.selected { border-color: #3b82f6; background: #1e3a5f; }

.es-detail {
background: #1e293b;
border-radius: 12px;
padding: 18px 20px;
border: 1px solid #3b82f6;
margin-bottom: 14px;
display: none;
}
.es-detail.visible { display: block; }
.es-detail-inner { display: flex; align-items: flex-start; gap: 20px; flex-wrap: wrap; }
.es-preview { font-size: 4rem; line-height: 1; flex-shrink: 0; }
.es-info { flex: 1; min-width: 200px; }
.es-info-name { font-size: 1.1rem; font-weight: 700; color: #bfdbfe; margin-bottom: 10px; }
.es-info-row {
display: flex; align-items: center; gap: 8px;
margin-bottom: 7px; flex-wrap: wrap;
}
.es-info-label { color: #64748b; font-size: 0.8rem; width: 90px; flex-shrink: 0; }
.es-info-val {
font-family: 'Courier New', monospace;
font-size: 0.88rem;
color: #93c5fd;
background: #0f172a;
padding: 3px 8px;
border-radius: 5px;
}
.es-copy-btn {
padding: 3px 10px;
border-radius: 6px;
border: 1px solid #3b82f6;
background: transparent;
color: #60a5fa;
font-size: 0.78rem;
cursor: pointer;
transition: background 0.15s;
}
.es-copy-btn:hover { background: #1e3a5f; }
.es-copy-emoji-btn {
margin-top: 10px;
padding: 8px 20px;
border-radius: 8px;
border: none;
background: #3b82f6;
color: #fff;
font-size: 0.95rem;
font-weight: 700;
cursor: pointer;
transition: background 0.2s;
}
.es-copy-emoji-btn:hover { background: #2563eb; }

.es-empty { color: #64748b; font-size: 0.95rem; text-align: center; padding: 20px 0; }

.es-toast {
position: fixed;
bottom: 24px; left: 50%;
transform: translateX(-50%) translateY(20px);
background: #1d4ed8;
color: #fff;
padding: 10px 22px;
border-radius: 10px;
font-size: 0.9rem;
font-weight: 600;
opacity: 0;
transition: opacity 0.25s, transform 0.25s;
pointer-events: none;
z-index: 9999;
white-space: nowrap;
}
.es-toast.show { opacity: 1; transform: translateX(-50%) translateY(0); }

.es-count { color: #64748b; font-size: 0.8rem; margin-bottom: 8px; }

@media (max-width: 600px) {
.es-hero { padding: 24px 16px; }
.es-hero h1 { font-size: 1.4rem; }
.es-cell { width: 38px; height: 38px; font-size: 1.3rem; }
.es-preview { font-size: 3rem; }
}
</style>

<div class="es-hero">
<h1>絵文字検索＆コピー</h1>
<p>1500以上の絵文字をキーワードで検索 — クリックでコピー</p>
</div>

<div class="es-search-row">
<input id="es-search" class="es-search" type="text" placeholder="絵文字を検索... (例: heart, fire, cat, 猫)" oninput="esjSearch()" autocomplete="off" spellcheck="false">
<div class="es-tone-wrap">
<span class="es-tone-label">肌色:</span>
<div class="es-tone-buttons">
<button class="es-tone-btn active" onclick="esjSetTone(this,'')" title="デフォルト">&#x270B;</button>
<button class="es-tone-btn" onclick="esjSetTone(this,'1F3FB')" title="明るい" style="background:#fde8cd">&#x270B;&#x1F3FB;</button>
<button class="es-tone-btn" onclick="esjSetTone(this,'1F3FC')" title="やや明るい" style="background:#f3c89a">&#x270B;&#x1F3FC;</button>
<button class="es-tone-btn" onclick="esjSetTone(this,'1F3FD')" title="中間" style="background:#d4a574">&#x270B;&#x1F3FD;</button>
<button class="es-tone-btn" onclick="esjSetTone(this,'1F3FE')" title="やや暗い" style="background:#a0714f">&#x270B;&#x1F3FE;</button>
<button class="es-tone-btn" onclick="esjSetTone(this,'1F3FF')" title="暗い" style="background:#5c3d2e">&#x270B;&#x1F3FF;</button>
</div>
</div>
</div>

<div class="es-tabs" id="esj-tabs"></div>

<div id="esj-recent-box" class="es-recent-box" style="display:none">
<div class="es-section-label">最近使った絵文字</div>
<div class="es-recent-row" id="esj-recent-row"></div>
</div>

<div id="esj-detail" class="es-detail">
<div class="es-detail-inner">
<div class="es-preview" id="esj-preview">&#x1F600;</div>
<div class="es-info">
<div class="es-info-name" id="esj-info-name">Grinning Face</div>
<div class="es-info-row">
<span class="es-info-label">Unicode</span>
<span class="es-info-val" id="esj-info-cp">U+1F600</span>
<button class="es-copy-btn" onclick="esjCopyVal('esj-info-cp')">コピー</button>
</div>
<div class="es-info-row">
<span class="es-info-label">HTMLエンティティ</span>
<span class="es-info-val" id="esj-info-html">&#amp;#128512;</span>
<button class="es-copy-btn" onclick="esjCopyVal('esj-info-html')">コピー</button>
</div>
<div class="es-info-row">
<span class="es-info-label">CSS値</span>
<span class="es-info-val" id="esj-info-css">\1F600</span>
<button class="es-copy-btn" onclick="esjCopyVal('esj-info-css')">コピー</button>
</div>
<button class="es-copy-emoji-btn" onclick="esjCopySelected()">絵文字をコピー</button>
</div>
</div>
</div>

<div class="es-grid-box">
<div class="es-count" id="esj-count"></div>
<div class="es-grid" id="esj-grid"></div>
<div class="es-empty" id="esj-empty" style="display:none">絵文字が見つかりません。別のキーワードで試してください。</div>
</div>

<div class="es-toast" id="esj-toast"></div>

<script>
(function() {
'use strict';

var ESJ = {
query: '',
cat: 'all',
tone: '',
selected: null,
recent: []
};

var ESJ_TONES = ['1F3FB','1F3FC','1F3FD','1F3FE','1F3FF'];

var ESJ_DATA = [
// Smileys & Emotion
['\u{1F600}','grinning face','smileys'],
['\u{1F603}','grinning face with big eyes','smileys'],
['\u{1F604}','grinning face with smiling eyes','smileys'],
['\u{1F601}','beaming face with smiling eyes','smileys'],
['\u{1F606}','grinning squinting face','smileys'],
['\u{1F605}','grinning face with sweat','smileys'],
['\u{1F923}','rolling on the floor laughing','smileys'],
['\u{1F602}','face with tears of joy','smileys'],
['\u{1F642}','slightly smiling face','smileys'],
['\u{1F643}','upside-down face','smileys'],
['\u{1FAE0}','melting face','smileys'],
['\u{1F609}','winking face','smileys'],
['\u{1F60A}','smiling face with smiling eyes','smileys'],
['\u{1F607}','smiling face with halo','smileys'],
['\u{1F970}','smiling face with hearts','smileys'],
['\u{1F60D}','smiling face with heart-eyes','smileys'],
['\u{1F929}','star-struck','smileys'],
['\u{1F618}','face blowing a kiss','smileys'],
['\u{1F617}','kissing face','smileys'],
['\u{263A}','smiling face','smileys'],
['\u{1F61A}','kissing face with closed eyes','smileys'],
['\u{1F619}','kissing face with smiling eyes','smileys'],
['\u{1F972}','smiling face with tear','smileys'],
['\u{1F60B}','face savoring food','smileys'],
['\u{1F61B}','face with tongue','smileys'],
['\u{1F61C}','winking face with tongue','smileys'],
['\u{1F92A}','zany face','smileys'],
['\u{1F61D}','squinting face with tongue','smileys'],
['\u{1F911}','money-mouth face','smileys'],
['\u{1F917}','smiling face with open hands','smileys'],
['\u{1F92D}','face with hand over mouth','smileys'],
['\u{1FAE2}','face with open eyes and hand over mouth','smileys'],
['\u{1FAE3}','face with peeking eye','smileys'],
['\u{1F92B}','shushing face','smileys'],
['\u{1F914}','thinking face','smileys'],
['\u{1FAE1}','saluting face','smileys'],
['\u{1F910}','zipper-mouth face','smileys'],
['\u{1F928}','face with raised eyebrow','smileys'],
['\u{1F610}','neutral face','smileys'],
['\u{1F611}','expressionless face','smileys'],
['\u{1F636}','face without mouth','smileys'],
['\u{1FAE5}','dotted line face','smileys'],
['\u{1F60F}','smirking face','smileys'],
['\u{1F612}','unamused face','smileys'],
['\u{1F644}','face with rolling eyes','smileys'],
['\u{1F62C}','grimacing face','smileys'],
['\u{1FAE4}','face with diagonal mouth','smileys'],
['\u{1F925}','lying face','smileys'],
['\u{1F60C}','relieved face','smileys'],
['\u{1F614}','pensive face','smileys'],
['\u{1F62A}','sleepy face','smileys'],
['\u{1F924}','drooling face','smileys'],
['\u{1F634}','sleeping face','smileys'],
['\u{1F637}','face with medical mask','smileys'],
['\u{1F912}','face with thermometer','smileys'],
['\u{1F915}','face with head-bandage','smileys'],
['\u{1F922}','nauseated face','smileys'],
['\u{1F92E}','face vomiting','smileys'],
['\u{1F927}','sneezing face','smileys'],
['\u{1F975}','hot face','smileys'],
['\u{1F976}','cold face','smileys'],
['\u{1F974}','woozy face','smileys'],
['\u{1F635}','face with crossed-out eyes','smileys'],
['\u{1F92F}','exploding head','smileys'],
['\u{1F920}','cowboy hat face','smileys'],
['\u{1F973}','partying face','smileys'],
['\u{1F978}','disguised face','smileys'],
['\u{1F60E}','smiling face with sunglasses','smileys'],
['\u{1F913}','nerd face','smileys'],
['\u{1F9D0}','face with monocle','smileys'],
['\u{1F615}','confused face','smileys'],
['\u{1FAE8}','shaking face','smileys'],
['\u{1F61F}','worried face','smileys'],
['\u{1F641}','slightly frowning face','smileys'],
['\u{2639}','frowning face','smileys'],
['\u{1F62E}','face with open mouth','smileys'],
['\u{1F62F}','hushed face','smileys'],
['\u{1F632}','astonished face','smileys'],
['\u{1F633}','flushed face','smileys'],
['\u{1F97A}','pleading face','smileys'],
['\u{1F979}','face holding back tears','smileys'],
['\u{1F626}','frowning face with open mouth','smileys'],
['\u{1F627}','anguished face','smileys'],
['\u{1F628}','fearful face','smileys'],
['\u{1F630}','anxious face with sweat','smileys'],
['\u{1F625}','sad but relieved face','smileys'],
['\u{1F622}','crying face','smileys'],
['\u{1F62D}','loudly crying face','smileys'],
['\u{1F631}','face screaming in fear','smileys'],
['\u{1F616}','confounded face','smileys'],
['\u{1F623}','persevering face','smileys'],
['\u{1F61E}','disappointed face','smileys'],
['\u{1F613}','downcast face with sweat','smileys'],
['\u{1F629}','weary face','smileys'],
['\u{1F62B}','tired face','smileys'],
['\u{1F971}','yawning face','smileys'],
['\u{1F624}','face with steam from nose','smileys'],
['\u{1F621}','enraged face','smileys'],
['\u{1F620}','angry face','smileys'],
['\u{1F92C}','face with symbols on mouth','smileys'],
['\u{1F608}','smiling face with horns','smileys'],
['\u{1F47F}','angry face with horns','smileys'],
['\u{1F480}','skull','smileys'],
['\u{2620}','skull and crossbones','smileys'],
['\u{1F4A9}','pile of poo','smileys'],
['\u{1F921}','clown face','smileys'],
['\u{1F479}','ogre','smileys'],
['\u{1F47A}','goblin','smileys'],
['\u{1F47B}','ghost','smileys'],
['\u{1F47D}','alien','smileys'],
['\u{1F47E}','alien monster','smileys'],
['\u{1F916}','robot','smileys'],
['\u{1F63A}','grinning cat','smileys'],
['\u{1F638}','grinning cat with smiling eyes','smileys'],
['\u{1F639}','cat with tears of joy','smileys'],
['\u{1F63B}','smiling cat with heart-eyes','smileys'],
['\u{1F63C}','cat with wry smile','smileys'],
['\u{1F63D}','kissing cat','smileys'],
['\u{1F640}','weary cat','smileys'],
['\u{1F63F}','crying cat','smileys'],
['\u{1F63E}','pouting cat','smileys'],
['\u{1F648}','see-no-evil monkey','smileys'],
['\u{1F649}','hear-no-evil monkey','smileys'],
['\u{1F64A}','speak-no-evil monkey','smileys'],
['\u{1F48C}','love letter','smileys'],
['\u{1F498}','heart with arrow','smileys'],
['\u{1F49D}','heart with ribbon','smileys'],
['\u{1F496}','sparkling heart','smileys'],
['\u{1F497}','growing heart','smileys'],
['\u{1F493}','beating heart','smileys'],
['\u{1F49E}','revolving hearts','smileys'],
['\u{1F495}','two hearts','smileys'],
['\u{1F49F}','heart decoration','smileys'],
['\u{2763}','heart exclamation','smileys'],
['\u{1F494}','broken heart','smileys'],
['\u{2764}','red heart','smileys'],
['\u{1FA77}','pink heart','smileys'],
['\u{1F9E1}','orange heart','smileys'],
['\u{1F49B}','yellow heart','smileys'],
['\u{1F49A}','green heart','smileys'],
['\u{1F499}','blue heart','smileys'],
['\u{1FA75}','light blue heart','smileys'],
['\u{1F49C}','purple heart','smileys'],
['\u{1F90E}','brown heart','smileys'],
['\u{1F5A4}','black heart','smileys'],
['\u{1FA76}','grey heart','smileys'],
['\u{1F90D}','white heart','smileys'],
['\u{1F48B}','kiss mark','smileys'],
['\u{1F4AF}','hundred points','smileys'],
['\u{1F4A5}','collision','smileys'],
['\u{1F4AB}','dizzy','smileys'],
['\u{1F4A6}','sweat droplets','smileys'],
['\u{1F4A8}','dashing away','smileys'],
['\u{1F4AC}','speech balloon','smileys'],
['\u{1F4AD}','thought balloon','smileys'],
['\u{1F4A4}','zzz','smileys'],
['\u{1F525}','fire','smileys'],
['\u{2728}','sparkles','smileys'],
['\u{1F31F}','glowing star','smileys'],
['\u{1F4A7}','droplet','smileys'],
// People & Body
['\u{1F44B}','waving hand','people'],
['\u{1F91A}','raised back of hand','people'],
['\u{1F590}','hand with fingers splayed','people'],
['\u{270B}','raised hand','people'],
['\u{1F596}','vulcan salute','people'],
['\u{1FAF1}','rightwards hand','people'],
['\u{1FAF2}','leftwards hand','people'],
['\u{1FAF3}','palm down hand','people'],
['\u{1FAF4}','palm up hand','people'],
['\u{1F44C}','ok hand','people'],
['\u{1F90F}','pinching hand','people'],
['\u{270C}','victory hand','people'],
['\u{1F91E}','crossed fingers','people'],
['\u{1F91F}','love-you gesture','people'],
['\u{1F918}','sign of the horns','people'],
['\u{1F919}','call me hand','people'],
['\u{1F448}','backhand index pointing left','people'],
['\u{1F449}','backhand index pointing right','people'],
['\u{1F446}','backhand index pointing up','people'],
['\u{1F595}','middle finger','people'],
['\u{1F447}','backhand index pointing down','people'],
['\u{261D}','index pointing up','people'],
['\u{1FAF5}','index pointing at the viewer','people'],
['\u{1F44D}','thumbs up','people'],
['\u{1F44E}','thumbs down','people'],
['\u{270A}','raised fist','people'],
['\u{1F44A}','oncoming fist','people'],
['\u{1F91B}','left-facing fist','people'],
['\u{1F91C}','right-facing fist','people'],
['\u{1F44F}','clapping hands','people'],
['\u{1F64C}','raising hands','people'],
['\u{1FAF6}','heart hands','people'],
['\u{1F450}','open hands','people'],
['\u{1F932}','palms up together','people'],
['\u{1F91D}','handshake','people'],
['\u{1F64F}','folded hands','people'],
['\u{270D}','writing hand','people'],
['\u{1F485}','nail polish','people'],
['\u{1F933}','selfie','people'],
['\u{1F4AA}','flexed biceps','people'],
['\u{1F9BE}','mechanical arm','people'],
['\u{1F9BF}','mechanical leg','people'],
['\u{1F9B5}','leg','people'],
['\u{1F9B6}','foot','people'],
['\u{1F442}','ear','people'],
['\u{1F9BB}','ear with hearing aid','people'],
['\u{1F443}','nose','people'],
['\u{1F9E0}','brain','people'],
['\u{1FAC0}','anatomical heart','people'],
['\u{1FAC1}','lungs','people'],
['\u{1F9B7}','tooth','people'],
['\u{1F9B4}','bone','people'],
['\u{1F440}','eyes','people'],
['\u{1F441}','eye','people'],
['\u{1F445}','tongue','people'],
['\u{1F444}','mouth','people'],
['\u{1FAE6}','biting lip','people'],
['\u{1F476}','baby','people'],
['\u{1F9D2}','child','people'],
['\u{1F466}','boy','people'],
['\u{1F467}','girl','people'],
['\u{1F9D1}','person','people'],
['\u{1F471}','person blond hair','people'],
['\u{1F468}','man','people'],
['\u{1F9D4}','person beard','people'],
['\u{1F469}','woman','people'],
['\u{1F9D3}','older person','people'],
['\u{1F474}','old man','people'],
['\u{1F475}','old woman','people'],
['\u{1F64D}','person frowning','people'],
['\u{1F64E}','person pouting','people'],
['\u{1F645}','person gesturing no','people'],
['\u{1F646}','person gesturing ok','people'],
['\u{1F481}','person tipping hand','people'],
['\u{1F64B}','person raising hand','people'],
['\u{1F9CF}','deaf person','people'],
['\u{1F647}','person bowing','people'],
['\u{1F926}','person facepalming','people'],
['\u{1F937}','person shrugging','people'],
['\u{1F9D1}\u{200D}\u{2695}','health worker','people'],
['\u{1F9D1}\u{200D}\u{1F393}','student','people'],
['\u{1F9D1}\u{200D}\u{1F3EB}','teacher','people'],
['\u{1F9D1}\u{200D}\u{2696}','judge','people'],
['\u{1F9D1}\u{200D}\u{1F33E}','farmer','people'],
['\u{1F9D1}\u{200D}\u{1F373}','cook','people'],
['\u{1F9D1}\u{200D}\u{1F527}','mechanic','people'],
['\u{1F9D1}\u{200D}\u{1F3ED}','factory worker','people'],
['\u{1F9D1}\u{200D}\u{1F4BC}','office worker','people'],
['\u{1F9D1}\u{200D}\u{1F52C}','scientist','people'],
['\u{1F9D1}\u{200D}\u{1F4BB}','technologist','people'],
['\u{1F9D1}\u{200D}\u{1F3A4}','singer','people'],
['\u{1F9D1}\u{200D}\u{1F3A8}','artist','people'],
['\u{1F9D1}\u{200D}\u{2708}','pilot','people'],
['\u{1F9D1}\u{200D}\u{1F680}','astronaut','people'],
['\u{1F9D1}\u{200D}\u{1F692}','firefighter','people'],
['\u{1F46E}','police officer','people'],
['\u{1F575}','detective','people'],
['\u{1F482}','guard','people'],
['\u{1F477}','construction worker','people'],
['\u{1F934}','prince','people'],
['\u{1F478}','princess','people'],
['\u{1F473}','person wearing turban','people'],
['\u{1F472}','person with skullcap','people'],
['\u{1F9D5}','woman with headscarf','people'],
['\u{1F935}','person in tuxedo','people'],
['\u{1F470}','person with veil','people'],
['\u{1F930}','pregnant woman','people'],
['\u{1F931}','breast-feeding','people'],
['\u{1F47C}','baby angel','people'],
['\u{1F385}','santa claus','people'],
['\u{1F936}','mrs claus','people'],
['\u{1F9D9}','mage','people'],
['\u{1F9DA}','fairy','people'],
['\u{1F9DB}','vampire','people'],
['\u{1F9DC}','merperson','people'],
['\u{1F9DD}','elf','people'],
['\u{1F9DE}','genie','people'],
['\u{1F9DF}','zombie','people'],
['\u{1F9CC}','troll','people'],
['\u{1F486}','person getting massage','people'],
['\u{1F487}','person getting haircut','people'],
['\u{1F6B6}','person walking','people'],
['\u{1F9CD}','person standing','people'],
['\u{1F9CE}','person kneeling','people'],
['\u{1F3C3}','person running','people'],
['\u{1F483}','woman dancing','people'],
['\u{1F57A}','man dancing','people'],
['\u{1F46F}','people with bunny ears','people'],
['\u{1F9D6}','person in steamy room','people'],
['\u{1F9D7}','person climbing','people'],
['\u{1F93A}','person fencing','people'],
['\u{1F3C7}','horse racing','people'],
['\u{26F7}','skier','people'],
['\u{1F3C2}','snowboarder','people'],
['\u{1F3CC}','person golfing','people'],
['\u{1F3C4}','person surfing','people'],
['\u{1F6A3}','person rowing boat','people'],
['\u{1F3CA}','person swimming','people'],
['\u{26F9}','person bouncing ball','people'],
['\u{1F3CB}','person lifting weights','people'],
['\u{1F6B4}','person biking','people'],
['\u{1F6B5}','person mountain biking','people'],
['\u{1F938}','person cartwheeling','people'],
['\u{1F93C}','people wrestling','people'],
['\u{1F93D}','person playing water polo','people'],
['\u{1F93E}','person playing handball','people'],
['\u{1F939}','person juggling','people'],
['\u{1F9D8}','person in lotus position','people'],
['\u{1F6C0}','person taking bath','people'],
['\u{1F6CC}','person in bed','people'],
['\u{1F46B}','woman and man holding hands','people'],
['\u{1F46C}','men holding hands','people'],
['\u{1F46D}','women holding hands','people'],
['\u{1F48F}','kiss','people'],
['\u{1F491}','couple with heart','people'],
['\u{1F46A}','family','people'],
// Animals & Nature
['\u{1F435}','monkey face','animals'],
['\u{1F412}','monkey','animals'],
['\u{1F98D}','gorilla','animals'],
['\u{1F9A7}','orangutan','animals'],
['\u{1F436}','dog face','animals'],
['\u{1F415}','dog','animals'],
['\u{1F429}','poodle','animals'],
['\u{1F43A}','wolf','animals'],
['\u{1F98A}','fox','animals'],
['\u{1F99D}','raccoon','animals'],
['\u{1F431}','cat face','animals'],
['\u{1F408}','cat','animals'],
['\u{1F408}\u{200D}\u{2B1B}','black cat','animals'],
['\u{1F981}','lion','animals'],
['\u{1F42F}','tiger face','animals'],
['\u{1F405}','tiger','animals'],
['\u{1F406}','leopard','animals'],
['\u{1F434}','horse face','animals'],
['\u{1F40E}','horse','animals'],
['\u{1F984}','unicorn','animals'],
['\u{1F993}','zebra','animals'],
['\u{1F98C}','deer','animals'],
['\u{1F9AC}','bison','animals'],
['\u{1F42E}','cow face','animals'],
['\u{1F404}','cow','animals'],
['\u{1F437}','pig face','animals'],
['\u{1F416}','pig','animals'],
['\u{1F417}','boar','animals'],
['\u{1F43D}','pig nose','animals'],
['\u{1F40F}','ram','animals'],
['\u{1F411}','ewe','animals'],
['\u{1F410}','goat','animals'],
['\u{1F42A}','camel','animals'],
['\u{1F42B}','two-hump camel','animals'],
['\u{1F999}','llama','animals'],
['\u{1F992}','giraffe','animals'],
['\u{1F418}','elephant','animals'],
['\u{1F9A3}','mammoth','animals'],
['\u{1F98F}','rhinoceros','animals'],
['\u{1F99B}','hippopotamus','animals'],
['\u{1F42D}','mouse face','animals'],
['\u{1F401}','mouse','animals'],
['\u{1F400}','rat','animals'],
['\u{1F439}','hamster','animals'],
['\u{1F430}','rabbit face','animals'],
['\u{1F407}','rabbit','animals'],
['\u{1F43F}','chipmunk','animals'],
['\u{1F9AB}','beaver','animals'],
['\u{1F994}','hedgehog','animals'],
['\u{1F987}','bat','animals'],
['\u{1F43B}','bear','animals'],
['\u{1F43B}\u{200D}\u{2744}','polar bear','animals'],
['\u{1F428}','koala','animals'],
['\u{1F43C}','panda','animals'],
['\u{1F9A5}','sloth','animals'],
['\u{1F9A6}','otter','animals'],
['\u{1F9A8}','skunk','animals'],
['\u{1F998}','kangaroo','animals'],
['\u{1F9A1}','badger','animals'],
['\u{1F43E}','paw prints','animals'],
['\u{1F983}','turkey','animals'],
['\u{1F414}','chicken','animals'],
['\u{1F413}','rooster','animals'],
['\u{1F423}','hatching chick','animals'],
['\u{1F424}','baby chick','animals'],
['\u{1F425}','front-facing baby chick','animals'],
['\u{1F426}','bird','animals'],
['\u{1F427}','penguin','animals'],
['\u{1F54A}','dove','animals'],
['\u{1F985}','eagle','animals'],
['\u{1F986}','duck','animals'],
['\u{1F9A2}','swan','animals'],
['\u{1F989}','owl','animals'],
['\u{1F9A4}','dodo','animals'],
['\u{1F9A9}','flamingo','animals'],
['\u{1F99A}','peacock','animals'],
['\u{1F99C}','parrot','animals'],
['\u{1F438}','frog','animals'],
['\u{1F40A}','crocodile','animals'],
['\u{1F422}','turtle','animals'],
['\u{1F98E}','lizard','animals'],
['\u{1F40D}','snake','animals'],
['\u{1F432}','dragon face','animals'],
['\u{1F409}','dragon','animals'],
['\u{1F995}','sauropod','animals'],
['\u{1F996}','T-Rex','animals'],
['\u{1F433}','spouting whale','animals'],
['\u{1F40B}','whale','animals'],
['\u{1F42C}','dolphin','animals'],
['\u{1F9AD}','seal','animals'],
['\u{1F41F}','fish','animals'],
['\u{1F420}','tropical fish','animals'],
['\u{1F421}','blowfish','animals'],
['\u{1F988}','shark','animals'],
['\u{1F419}','octopus','animals'],
['\u{1F41A}','spiral shell','animals'],
['\u{1F40C}','snail','animals'],
['\u{1F98B}','butterfly','animals'],
['\u{1F41B}','bug','animals'],
['\u{1F41C}','ant','animals'],
['\u{1F41D}','honeybee','animals'],
['\u{1FAB2}','beetle','animals'],
['\u{1F41E}','lady beetle','animals'],
['\u{1F997}','cricket','animals'],
['\u{1FAB3}','cockroach','animals'],
['\u{1F577}','spider','animals'],
['\u{1F578}','spider web','animals'],
['\u{1F982}','scorpion','animals'],
['\u{1FAB0}','fly','animals'],
['\u{1FAB1}','worm','animals'],
['\u{1F9A0}','microbe','animals'],
['\u{1F490}','bouquet','animals'],
['\u{1F338}','cherry blossom','animals'],
['\u{1F4AE}','white flower','animals'],
['\u{1FAB7}','lotus','animals'],
['\u{1F339}','rose','animals'],
['\u{1F940}','wilted flower','animals'],
['\u{1F33A}','hibiscus','animals'],
['\u{1F33B}','sunflower','animals'],
['\u{1F33C}','blossom','animals'],
['\u{1F337}','tulip','animals'],
['\u{1FABB}','hyacinth','animals'],
['\u{1F331}','seedling','animals'],
['\u{1FAB4}','potted plant','animals'],
['\u{1F332}','evergreen tree','animals'],
['\u{1F333}','deciduous tree','animals'],
['\u{1F334}','palm tree','animals'],
['\u{1F335}','cactus','animals'],
['\u{1F33E}','sheaf of rice','animals'],
['\u{1F33F}','herb','animals'],
['\u{2618}','shamrock','animals'],
['\u{1F340}','four leaf clover','animals'],
['\u{1F341}','maple leaf','animals'],
['\u{1F342}','fallen leaf','animals'],
['\u{1F343}','leaf fluttering in wind','animals'],
['\u{1F344}','mushroom','animals'],
['\u{1F30B}','volcano','animals'],
['\u{1F5FB}','mount fuji','animals'],
['\u{26F0}','mountain','animals'],
['\u{1F3D4}','snow-capped mountain','animals'],
['\u{1F3D6}','beach with umbrella','animals'],
['\u{1F307}','sunset','animals'],
['\u{1F303}','night with stars','animals'],
['\u{1F304}','sunrise over mountains','animals'],
['\u{1F305}','sunrise','animals'],
['\u{1F308}','rainbow','animals'],
['\u{2614}','umbrella with rain drops','animals'],
['\u{26C4}','snowman','animals'],
['\u{2744}','snowflake','animals'],
['\u{2600}','sun','animals'],
['\u{1F319}','crescent moon','animals'],
['\u{1F315}','full moon','animals'],
['\u{2B50}','star','animals'],
['\u{1F30A}','water wave','animals'],
['\u{26A1}','lightning','animals'],
['\u{1F300}','cyclone','animals'],
['\u{1F327}','cloud with rain','animals'],
['\u{1F32A}','tornado','animals'],
// Food & Drink
['\u{1F347}','grapes','food'],
['\u{1F348}','melon','food'],
['\u{1F349}','watermelon','food'],
['\u{1F34A}','tangerine','food'],
['\u{1F34B}','lemon','food'],
['\u{1F34C}','banana','food'],
['\u{1F34D}','pineapple','food'],
['\u{1F96D}','mango','food'],
['\u{1F34E}','red apple','food'],
['\u{1F34F}','green apple','food'],
['\u{1F350}','pear','food'],
['\u{1F351}','peach','food'],
['\u{1F352}','cherries','food'],
['\u{1F353}','strawberry','food'],
['\u{1FAD0}','blueberries','food'],
['\u{1F95D}','kiwi fruit','food'],
['\u{1F345}','tomato','food'],
['\u{1F951}','avocado','food'],
['\u{1F346}','eggplant','food'],
['\u{1F954}','potato','food'],
['\u{1F955}','carrot','food'],
['\u{1F33D}','ear of corn','food'],
['\u{1F336}','hot pepper','food'],
['\u{1FAD1}','bell pepper','food'],
['\u{1F952}','cucumber','food'],
['\u{1F966}','broccoli','food'],
['\u{1F9C4}','garlic','food'],
['\u{1F9C5}','onion','food'],
['\u{1F344}','mushroom','food'],
['\u{1F35E}','bread','food'],
['\u{1F950}','croissant','food'],
['\u{1F956}','baguette bread','food'],
['\u{1F968}','pretzel','food'],
['\u{1F96F}','bagel','food'],
['\u{1F95E}','pancakes','food'],
['\u{1F9C7}','waffle','food'],
['\u{1F9C0}','cheese wedge','food'],
['\u{1F356}','meat on bone','food'],
['\u{1F357}','poultry leg','food'],
['\u{1F969}','cut of meat','food'],
['\u{1F953}','bacon','food'],
['\u{1F354}','hamburger','food'],
['\u{1F35F}','french fries','food'],
['\u{1F355}','pizza','food'],
['\u{1F32D}','hot dog','food'],
['\u{1F96A}','sandwich','food'],
['\u{1F959}','stuffed flatbread','food'],
['\u{1F9C6}','falafel','food'],
['\u{1F95A}','egg','food'],
['\u{1F373}','cooking','food'],
['\u{1F372}','pot of food','food'],
['\u{1F963}','bowl with spoon','food'],
['\u{1F957}','green salad','food'],
['\u{1F37F}','popcorn','food'],
['\u{1F371}','bento box','food'],
['\u{1F358}','rice cracker','food'],
['\u{1F359}','rice ball','food'],
['\u{1F35A}','cooked rice','food'],
['\u{1F35B}','curry rice','food'],
['\u{1F35C}','steaming bowl','food'],
['\u{1F35D}','spaghetti','food'],
['\u{1F360}','roasted sweet potato','food'],
['\u{1F362}','oden','food'],
['\u{1F363}','sushi','food'],
['\u{1F364}','fried shrimp','food'],
['\u{1F365}','fish cake with swirl','food'],
['\u{1F361}','dango','food'],
['\u{1F95F}','dumpling','food'],
['\u{1F960}','fortune cookie','food'],
['\u{1F961}','takeout box','food'],
['\u{1F980}','crab','food'],
['\u{1F99E}','lobster','food'],
['\u{1F990}','shrimp','food'],
['\u{1F991}','squid','food'],
['\u{1F9AA}','oyster','food'],
['\u{1F366}','soft ice cream','food'],
['\u{1F367}','shaved ice','food'],
['\u{1F368}','ice cream','food'],
['\u{1F369}','doughnut','food'],
['\u{1F36A}','cookie','food'],
['\u{1F382}','birthday cake','food'],
['\u{1F370}','shortcake','food'],
['\u{1F9C1}','cupcake','food'],
['\u{1F967}','pie','food'],
['\u{1F36B}','chocolate bar','food'],
['\u{1F36C}','candy','food'],
['\u{1F36D}','lollipop','food'],
['\u{1F36F}','honey pot','food'],
['\u{1F37C}','baby bottle','food'],
['\u{1F95B}','glass of milk','food'],
['\u{2615}','hot beverage','food'],
['\u{1FAD6}','teapot','food'],
['\u{1F375}','teacup without handle','food'],
['\u{1F376}','sake','food'],
['\u{1F37E}','bottle with popping cork','food'],
['\u{1F377}','wine glass','food'],
['\u{1F378}','cocktail glass','food'],
['\u{1F379}','tropical drink','food'],
['\u{1F37A}','beer mug','food'],
['\u{1F37B}','clinking beer mugs','food'],
['\u{1F942}','clinking glasses','food'],
['\u{1F943}','tumbler glass','food'],
['\u{1F964}','cup with straw','food'],
['\u{1F9CB}','bubble tea','food'],
['\u{1F374}','fork and knife','food'],
['\u{1F944}','spoon','food'],
['\u{1F52A}','kitchen knife','food'],
['\u{1F3FA}','amphora','food'],
// Travel & Places
['\u{1F5FA}','world map','travel'],
['\u{1F9ED}','compass','travel'],
['\u{1F3D4}','snow-capped mountain','travel'],
['\u{1F3D6}','beach with umbrella','travel'],
['\u{1F3DC}','desert','travel'],
['\u{1F3DD}','desert island','travel'],
['\u{1F3DE}','national park','travel'],
['\u{1F3DF}','stadium','travel'],
['\u{1F3DB}','classical building','travel'],
['\u{1F3D7}','building construction','travel'],
['\u{1F6D6}','hut','travel'],
['\u{1F3D8}','houses','travel'],
['\u{1F3E0}','house','travel'],
['\u{1F3E1}','house with garden','travel'],
['\u{1F3E2}','office building','travel'],
['\u{1F3E5}','hospital','travel'],
['\u{1F3E6}','bank','travel'],
['\u{1F3E8}','hotel','travel'],
['\u{1F3EA}','convenience store','travel'],
['\u{1F3EB}','school','travel'],
['\u{1F3EC}','department store','travel'],
['\u{1F3ED}','factory','travel'],
['\u{1F5FC}','tokyo tower','travel'],
['\u{1F5FD}','statue of liberty','travel'],
['\u{26EA}','church','travel'],
['\u{1F54C}','mosque','travel'],
['\u{1F54D}','synagogue','travel'],
['\u{1F54B}','kaaba','travel'],
['\u{26F2}','fountain','travel'],
['\u{26FA}','tent','travel'],
['\u{1F301}','foggy','travel'],
['\u{1F303}','night with stars','travel'],
['\u{1F3D9}','cityscape','travel'],
['\u{2668}','hot springs','travel'],
['\u{1F682}','locomotive','travel'],
['\u{1F683}','railway car','travel'],
['\u{1F684}','high-speed train','travel'],
['\u{1F685}','bullet train','travel'],
['\u{1F686}','train','travel'],
['\u{1F687}','metro','travel'],
['\u{1F689}','station','travel'],
['\u{1F68C}','bus','travel'],
['\u{1F691}','ambulance','travel'],
['\u{1F692}','fire engine','travel'],
['\u{1F693}','police car','travel'],
['\u{1F695}','taxi','travel'],
['\u{1F697}','automobile','travel'],
['\u{1F699}','sport utility vehicle','travel'],
['\u{1F6FB}','pickup truck','travel'],
['\u{1F69A}','delivery truck','travel'],
['\u{1F3CE}','racing car','travel'],
['\u{1F3CD}','motorcycle','travel'],
['\u{1F6F5}','motor scooter','travel'],
['\u{1F6B2}','bicycle','travel'],
['\u{1F6F4}','kick scooter','travel'],
['\u{1F6F9}','skateboard','travel'],
['\u{26FD}','fuel pump','travel'],
['\u{1F6A8}','police car light','travel'],
['\u{1F6D1}','stop sign','travel'],
['\u{2693}','anchor','travel'],
['\u{26F5}','sailboat','travel'],
['\u{1F6A4}','speedboat','travel'],
['\u{1F6A2}','ship','travel'],
['\u{2708}','airplane','travel'],
['\u{1F6EB}','airplane departure','travel'],
['\u{1F6EC}','airplane arrival','travel'],
['\u{1FA82}','parachute','travel'],
['\u{1F4BA}','seat','travel'],
['\u{1F681}','helicopter','travel'],
['\u{1F6F0}','satellite','travel'],
['\u{1F680}','rocket','travel'],
['\u{1F6F8}','flying saucer','travel'],
['\u{231B}','hourglass done','travel'],
['\u{23F3}','hourglass not done','travel'],
['\u{231A}','watch','travel'],
['\u{23F0}','alarm clock','travel'],
['\u{23F1}','stopwatch','travel'],
// Activities
['\u{1F383}','jack-o-lantern','activities'],
['\u{1F384}','christmas tree','activities'],
['\u{1F386}','fireworks','activities'],
['\u{1F387}','sparkler','activities'],
['\u{1F9E8}','firecracker','activities'],
['\u{2728}','sparkles','activities'],
['\u{1F388}','balloon','activities'],
['\u{1F389}','party popper','activities'],
['\u{1F38A}','confetti ball','activities'],
['\u{1F380}','ribbon','activities'],
['\u{1F381}','wrapped gift','activities'],
['\u{1F3C6}','trophy','activities'],
['\u{1F3C5}','sports medal','activities'],
['\u{1F947}','1st place medal','activities'],
['\u{1F948}','2nd place medal','activities'],
['\u{1F949}','3rd place medal','activities'],
['\u{26BD}','soccer ball','activities'],
['\u{26BE}','baseball','activities'],
['\u{1F94E}','softball','activities'],
['\u{1F3C0}','basketball','activities'],
['\u{1F3D0}','volleyball','activities'],
['\u{1F3C8}','american football','activities'],
['\u{1F3C9}','rugby football','activities'],
['\u{1F3BE}','tennis','activities'],
['\u{1F94F}','flying disc','activities'],
['\u{1F3B3}','bowling','activities'],
['\u{1F3CF}','cricket game','activities'],
['\u{1F3D1}','field hockey','activities'],
['\u{1F3D2}','ice hockey','activities'],
['\u{1F94D}','lacrosse','activities'],
['\u{1F3D3}','ping pong','activities'],
['\u{1F3F8}','badminton','activities'],
['\u{1F94A}','boxing glove','activities'],
['\u{1F94B}','martial arts uniform','activities'],
['\u{1F945}','goal net','activities'],
['\u{26F3}','flag in hole','activities'],
['\u{26F8}','ice skate','activities'],
['\u{1F3A3}','fishing pole','activities'],
['\u{1F3BF}','skis','activities'],
['\u{1F6F7}','sled','activities'],
['\u{1F3AF}','bullseye','activities'],
['\u{1FA80}','yo-yo','activities'],
['\u{1FA81}','kite','activities'],
['\u{1F3B1}','pool 8 ball','activities'],
['\u{1F52E}','crystal ball','activities'],
['\u{1FA84}','magic wand','activities'],
['\u{1F9FF}','nazar amulet','activities'],
['\u{1F3AE}','video game','activities'],
['\u{1F579}','joystick','activities'],
['\u{1F3B0}','slot machine','activities'],
['\u{1F3B2}','game die','activities'],
['\u{1F9E9}','puzzle piece','activities'],
['\u{1F9F8}','teddy bear','activities'],
['\u{2660}','spade suit','activities'],
['\u{2665}','heart suit','activities'],
['\u{2666}','diamond suit','activities'],
['\u{2663}','club suit','activities'],
['\u{1F3AD}','performing arts','activities'],
['\u{1F5BC}','framed picture','activities'],
['\u{1F3A8}','artist palette','activities'],
['\u{1F9F5}','thread','activities'],
['\u{1F9F6}','yarn','activities'],
// Objects
['\u{1F453}','glasses','objects'],
['\u{1F576}','sunglasses','objects'],
['\u{1F454}','necktie','objects'],
['\u{1F455}','t-shirt','objects'],
['\u{1F456}','jeans','objects'],
['\u{1F9E3}','scarf','objects'],
['\u{1F9E4}','gloves','objects'],
['\u{1F9E5}','coat','objects'],
['\u{1F9E6}','socks','objects'],
['\u{1F457}','dress','objects'],
['\u{1F458}','kimono','objects'],
['\u{1F97B}','sari','objects'],
['\u{1F459}','bikini','objects'],
['\u{1F45A}','womans clothes','objects'],
['\u{1F45B}','purse','objects'],
['\u{1F45C}','handbag','objects'],
['\u{1F45D}','clutch bag','objects'],
['\u{1F6CD}','shopping bags','objects'],
['\u{1F392}','backpack','objects'],
['\u{1F45E}','mans shoe','objects'],
['\u{1F45F}','running shoe','objects'],
['\u{1F97E}','hiking boot','objects'],
['\u{1F460}','high-heeled shoe','objects'],
['\u{1F461}','womans sandal','objects'],
['\u{1F462}','womans boot','objects'],
['\u{1F451}','crown','objects'],
['\u{1F452}','womans hat','objects'],
['\u{1F3A9}','top hat','objects'],
['\u{1F9E2}','billed cap','objects'],
['\u{26D1}','rescue workers helmet','objects'],
['\u{1F484}','lipstick','objects'],
['\u{1F48D}','ring','objects'],
['\u{1F48E}','gem stone','objects'],
['\u{1F507}','muted speaker','objects'],
['\u{1F508}','speaker low volume','objects'],
['\u{1F509}','speaker medium volume','objects'],
['\u{1F50A}','speaker high volume','objects'],
['\u{1F4E2}','loudspeaker','objects'],
['\u{1F4E3}','megaphone','objects'],
['\u{1F514}','bell','objects'],
['\u{1F515}','bell with slash','objects'],
['\u{1F3BC}','musical score','objects'],
['\u{1F3B5}','musical note','objects'],
['\u{1F3B6}','musical notes','objects'],
['\u{1F399}','studio microphone','objects'],
['\u{1F3A4}','microphone','objects'],
['\u{1F3A7}','headphone','objects'],
['\u{1F4FB}','radio','objects'],
['\u{1F3B7}','saxophone','objects'],
['\u{1F3B8}','guitar','objects'],
['\u{1F3B9}','musical keyboard','objects'],
['\u{1F3BA}','trumpet','objects'],
['\u{1F3BB}','violin','objects'],
['\u{1FA95}','banjo','objects'],
['\u{1F941}','drum','objects'],
['\u{1F4F1}','mobile phone','objects'],
['\u{260E}','telephone','objects'],
['\u{1F4DE}','telephone receiver','objects'],
['\u{1F4E0}','fax machine','objects'],
['\u{1F50B}','battery','objects'],
['\u{1F50C}','electric plug','objects'],
['\u{1F4BB}','laptop','objects'],
['\u{1F5A5}','desktop computer','objects'],
['\u{1F5A8}','printer','objects'],
['\u{2328}','keyboard','objects'],
['\u{1F4BD}','computer disk','objects'],
['\u{1F4BE}','floppy disk','objects'],
['\u{1F4BF}','optical disk','objects'],
['\u{1F4C0}','dvd','objects'],
['\u{1F9EE}','abacus','objects'],
['\u{1F3A5}','movie camera','objects'],
['\u{1F4FA}','television','objects'],
['\u{1F4F7}','camera','objects'],
['\u{1F4F8}','camera with flash','objects'],
['\u{1F4F9}','video camera','objects'],
['\u{1F4FC}','videocassette','objects'],
['\u{1F50D}','magnifying glass tilted left','objects'],
['\u{1F50E}','magnifying glass tilted right','objects'],
['\u{1F56F}','candle','objects'],
['\u{1F4A1}','light bulb','objects'],
['\u{1F526}','flashlight','objects'],
['\u{1F3EE}','red paper lantern','objects'],
['\u{1F4D4}','notebook with decorative cover','objects'],
['\u{1F4D5}','closed book','objects'],
['\u{1F4D6}','open book','objects'],
['\u{1F4D7}','green book','objects'],
['\u{1F4D8}','blue book','objects'],
['\u{1F4D9}','orange book','objects'],
['\u{1F4DA}','books','objects'],
['\u{1F4D3}','notebook','objects'],
['\u{1F4C3}','page with curl','objects'],
['\u{1F4DC}','scroll','objects'],
['\u{1F4C4}','page facing up','objects'],
['\u{1F4F0}','newspaper','objects'],
['\u{1F4D1}','bookmark tabs','objects'],
['\u{1F516}','bookmark','objects'],
['\u{1F4B0}','money bag','objects'],
['\u{1FA99}','coin','objects'],
['\u{1F4B4}','yen banknote','objects'],
['\u{1F4B5}','dollar banknote','objects'],
['\u{1F4B6}','euro banknote','objects'],
['\u{1F4B7}','pound banknote','objects'],
['\u{1F4B8}','money with wings','objects'],
['\u{1F4B3}','credit card','objects'],
['\u{1F9FE}','receipt','objects'],
['\u{1F4B9}','chart increasing with yen','objects'],
['\u{1F4E7}','e-mail','objects'],
['\u{1F4E8}','incoming envelope','objects'],
['\u{1F4E9}','envelope with arrow','objects'],
['\u{1F4E6}','package','objects'],
['\u{1F4EB}','closed mailbox with raised flag','objects'],
['\u{1F4EC}','open mailbox with raised flag','objects'],
['\u{270F}','pencil','objects'],
['\u{2712}','black nib','objects'],
['\u{1F58B}','fountain pen','objects'],
['\u{1F58A}','pen','objects'],
['\u{1F58C}','paintbrush','objects'],
['\u{1F58D}','crayon','objects'],
['\u{1F4DD}','memo','objects'],
['\u{1F4BC}','briefcase','objects'],
['\u{1F4C1}','file folder','objects'],
['\u{1F4C2}','open file folder','objects'],
['\u{1F4C5}','calendar','objects'],
['\u{1F4C6}','tear-off calendar','objects'],
['\u{1F4C7}','card index','objects'],
['\u{1F4C8}','chart increasing','objects'],
['\u{1F4C9}','chart decreasing','objects'],
['\u{1F4CA}','bar chart','objects'],
['\u{1F4CB}','clipboard','objects'],
['\u{1F4CC}','pushpin','objects'],
['\u{1F4CD}','round pushpin','objects'],
['\u{1F4CE}','paperclip','objects'],
['\u{1F4CF}','straight ruler','objects'],
['\u{1F4D0}','triangular ruler','objects'],
['\u{2702}','scissors','objects'],
['\u{1F512}','locked','objects'],
['\u{1F513}','unlocked','objects'],
['\u{1F511}','key','objects'],
['\u{1F5DD}','old key','objects'],
['\u{1F528}','hammer','objects'],
['\u{1FA93}','axe','objects'],
['\u{2692}','hammer and pick','objects'],
['\u{1F6E0}','hammer and wrench','objects'],
['\u{2694}','crossed swords','objects'],
['\u{1F4A3}','bomb','objects'],
['\u{1FA83}','boomerang','objects'],
['\u{1F3F9}','bow and arrow','objects'],
['\u{1F527}','wrench','objects'],
['\u{1F529}','nut and bolt','objects'],
['\u{2699}','gear','objects'],
['\u{1F9F0}','toolbox','objects'],
['\u{1F9F2}','magnet','objects'],
['\u{1FA9C}','ladder','objects'],
['\u{2697}','alembic','objects'],
['\u{1F9EA}','test tube','objects'],
['\u{1F9EC}','dna','objects'],
['\u{1F52C}','microscope','objects'],
['\u{1F52D}','telescope','objects'],
['\u{1F4E1}','satellite antenna','objects'],
['\u{1F489}','syringe','objects'],
['\u{1F48A}','pill','objects'],
['\u{1FA79}','adhesive bandage','objects'],
['\u{1FA7A}','stethoscope','objects'],
['\u{1F6AA}','door','objects'],
['\u{1F6CF}','bed','objects'],
['\u{1F6CB}','couch and lamp','objects'],
['\u{1FA91}','chair','objects'],
['\u{1F6BD}','toilet','objects'],
['\u{1F6BF}','shower','objects'],
['\u{1F6C1}','bathtub','objects'],
['\u{1FAA5}','toothbrush','objects'],
['\u{1F9F4}','lotion bottle','objects'],
['\u{1F9F7}','safety pin','objects'],
['\u{1F9F9}','broom','objects'],
['\u{1F9FA}','basket','objects'],
['\u{1F9FB}','roll of paper','objects'],
['\u{1FAA3}','bucket','objects'],
['\u{1F9FC}','soap','objects'],
['\u{1F9FD}','sponge','objects'],
['\u{1F9EF}','fire extinguisher','objects'],
['\u{1F6D2}','shopping cart','objects'],
['\u{1F5FF}','moai','objects'],
// Symbols
['\u{267F}','wheelchair symbol','symbols'],
['\u{26A0}','warning','symbols'],
['\u{26D4}','no entry','symbols'],
['\u{1F6AB}','prohibited','symbols'],
['\u{1F51E}','no one under eighteen','symbols'],
['\u{2622}','radioactive','symbols'],
['\u{2623}','biohazard','symbols'],
['\u{2B06}','up arrow','symbols'],
['\u{2197}','up-right arrow','symbols'],
['\u{27A1}','right arrow','symbols'],
['\u{2198}','down-right arrow','symbols'],
['\u{2B07}','down arrow','symbols'],
['\u{2199}','down-left arrow','symbols'],
['\u{2B05}','left arrow','symbols'],
['\u{2196}','up-left arrow','symbols'],
['\u{2195}','up-down arrow','symbols'],
['\u{2194}','left-right arrow','symbols'],
['\u{21A9}','right arrow curving left','symbols'],
['\u{21AA}','left arrow curving right','symbols'],
['\u{1F519}','back arrow','symbols'],
['\u{1F51A}','end arrow','symbols'],
['\u{1F51B}','on arrow','symbols'],
['\u{1F51C}','soon arrow','symbols'],
['\u{1F51D}','top arrow','symbols'],
['\u{1F6D0}','place of worship','symbols'],
['\u{269B}','atom symbol','symbols'],
['\u{2721}','star of david','symbols'],
['\u{2638}','wheel of dharma','symbols'],
['\u{262F}','yin yang','symbols'],
['\u{271D}','latin cross','symbols'],
['\u{262A}','star and crescent','symbols'],
['\u{262E}','peace symbol','symbols'],
['\u{2648}','aries','symbols'],
['\u{2649}','taurus','symbols'],
['\u{264A}','gemini','symbols'],
['\u{264B}','cancer','symbols'],
['\u{264C}','leo','symbols'],
['\u{264D}','virgo','symbols'],
['\u{264E}','libra','symbols'],
['\u{264F}','scorpio','symbols'],
['\u{2650}','sagittarius','symbols'],
['\u{2651}','capricorn','symbols'],
['\u{2652}','aquarius','symbols'],
['\u{2653}','pisces','symbols'],
['\u{1F500}','shuffle tracks button','symbols'],
['\u{1F501}','repeat button','symbols'],
['\u{25B6}','play button','symbols'],
['\u{23E9}','fast-forward button','symbols'],
['\u{25C0}','reverse button','symbols'],
['\u{23EA}','fast reverse button','symbols'],
['\u{23F8}','pause button','symbols'],
['\u{23F9}','stop button','symbols'],
['\u{23FA}','record button','symbols'],
['\u{1F3A6}','cinema','symbols'],
['\u{1F4F3}','vibration mode','symbols'],
['\u{1F4F4}','mobile phone off','symbols'],
['\u{2640}','female sign','symbols'],
['\u{2642}','male sign','symbols'],
['\u{26A7}','transgender symbol','symbols'],
['\u{2716}','multiply','symbols'],
['\u{2795}','plus','symbols'],
['\u{2796}','minus','symbols'],
['\u{2797}','divide','symbols'],
['\u{267E}','infinity','symbols'],
['\u{203C}','double exclamation mark','symbols'],
['\u{2049}','exclamation question mark','symbols'],
['\u{2753}','red question mark','symbols'],
['\u{2755}','white exclamation mark','symbols'],
['\u{2757}','red exclamation mark','symbols'],
['\u{1F4B1}','currency exchange','symbols'],
['\u{1F4B2}','heavy dollar sign','symbols'],
['\u{2747}','sparkle','symbols'],
['\u{274E}','cross mark','symbols'],
['\u{2705}','check mark button','symbols'],
['\u{1F7E0}','orange circle','symbols'],
['\u{1F7E1}','yellow circle','symbols'],
['\u{1F7E2}','green circle','symbols'],
['\u{1F7E3}','purple circle','symbols'],
['\u{1F7E4}','brown circle','symbols'],
['\u{26AA}','white circle','symbols'],
['\u{26AB}','black circle','symbols'],
['\u{1F534}','red circle','symbols'],
['\u{1F535}','blue circle','symbols'],
['\u{1F536}','large orange diamond','symbols'],
['\u{1F537}','large blue diamond','symbols'],
['\u{1F53A}','red triangle pointed up','symbols'],
['\u{1F53B}','red triangle pointed down','symbols'],
['\u{1F518}','radio button','symbols'],
['\u{25AA}','black small square','symbols'],
['\u{25AB}','white small square','symbols'],
['\u{2B1B}','black large square','symbols'],
['\u{2B1C}','white large square','symbols'],
['\u{1F7E5}','red square','symbols'],
['\u{1F7E6}','blue square','symbols'],
['\u{1F7E7}','orange square','symbols'],
['\u{1F7E8}','yellow square','symbols'],
['\u{1F7E9}','green square','symbols'],
['\u{1F7EA}','purple square','symbols'],
['\u{1F7EB}','brown square','symbols'],
['\u{2B50}','star','symbols'],
// Flags
['\u{1F3C1}','chequered flag','flags'],
['\u{1F6A9}','triangular flag','flags'],
['\u{1F38C}','crossed flags','flags'],
['\u{1F3F4}','black flag','flags'],
['\u{1F3F3}','white flag','flags'],
['\u{1F3F3}\u{FE0F}\u{200D}\u{1F308}','rainbow flag','flags'],
['\u{1F3F3}\u{FE0F}\u{200D}\u{26A7}\u{FE0F}','transgender flag','flags'],
['\u{1F1FA}\u{1F1F8}','flag United States','flags'],
['\u{1F1EC}\u{1F1E7}','flag United Kingdom','flags'],
['\u{1F1EF}\u{1F1F5}','flag Japan','flags'],
['\u{1F1E8}\u{1F1E6}','flag Canada','flags'],
['\u{1F1E6}\u{1F1FA}','flag Australia','flags'],
['\u{1F1E9}\u{1F1EA}','flag Germany','flags'],
['\u{1F1EB}\u{1F1F7}','flag France','flags'],
['\u{1F1EE}\u{1F1F9}','flag Italy','flags'],
['\u{1F1EA}\u{1F1F8}','flag Spain','flags'],
['\u{1F1F0}\u{1F1F7}','flag South Korea','flags'],
['\u{1F1E8}\u{1F1F3}','flag China','flags'],
['\u{1F1E7}\u{1F1F7}','flag Brazil','flags'],
['\u{1F1EE}\u{1F1F3}','flag India','flags'],
['\u{1F1F2}\u{1F1FD}','flag Mexico','flags'],
['\u{1F1F7}\u{1F1FA}','flag Russia','flags'],
['\u{1F1F3}\u{1F1F1}','flag Netherlands','flags'],
['\u{1F1F8}\u{1F1EA}','flag Sweden','flags'],
['\u{1F1F9}\u{1F1F7}','flag Turkey','flags'],
['\u{1F1FA}\u{1F1E6}','flag Ukraine','flags'],
['\u{1F1F8}\u{1F1EC}','flag Singapore','flags'],
['\u{1F1F9}\u{1F1FC}','flag Taiwan','flags'],
['\u{1F3F4}\u{E0067}\u{E0062}\u{E0065}\u{E006E}\u{E0067}\u{E007F}','flag England','flags'],
['\u{1F3F4}\u{E0067}\u{E0062}\u{E0073}\u{E0063}\u{E0074}\u{E007F}','flag Scotland','flags'],
['\u{1F3F4}\u{E0067}\u{E0062}\u{E0077}\u{E006C}\u{E0073}\u{E007F}','flag Wales','flags'],
];

var ESJ_CATS = [
{ id: 'all',        label: 'すべて',       icon: '\u{1F50D}' },
{ id: 'smileys',    label: '顔・感情',     icon: '\u{1F600}' },
{ id: 'people',     label: '人・体',       icon: '\u{1F44B}' },
{ id: 'animals',    label: '動物・自然',   icon: '\u{1F42D}' },
{ id: 'food',       label: '食べ物・飲み物', icon: '\u{1F354}' },
{ id: 'travel',     label: '旅行・場所',   icon: '\u{2708}' },
{ id: 'activities', label: 'アクティビティ', icon: '\u{26BD}' },
{ id: 'objects',    label: 'モノ',         icon: '\u{1F4BB}' },
{ id: 'symbols',    label: '記号',         icon: '\u{2764}' },
{ id: 'flags',      label: '旗',           icon: '\u{1F3F3}' },
];

var ESJ_TONE_BASE = [
'\u{1F44B}','\u{1F91A}','\u{270B}','\u{1F590}','\u{1F596}','\u{1F44C}','\u{270C}','\u{1F91E}','\u{1F91F}','\u{1F918}','\u{1F919}',
'\u{1F448}','\u{1F449}','\u{1F446}','\u{1F595}','\u{1F447}','\u{261D}','\u{1F44D}','\u{1F44E}','\u{270A}','\u{1F44A}','\u{1F91B}','\u{1F91C}',
'\u{1F44F}','\u{1F64C}','\u{1F450}','\u{1F932}','\u{1F64F}','\u{270D}','\u{1F485}','\u{1F933}','\u{1F4AA}','\u{1F9B5}','\u{1F9B6}',
'\u{1F476}','\u{1F9D2}','\u{1F466}','\u{1F467}','\u{1F9D1}','\u{1F471}','\u{1F468}','\u{1F469}','\u{1F9D3}','\u{1F474}','\u{1F475}',
'\u{1F64D}','\u{1F64E}','\u{1F645}','\u{1F646}','\u{1F481}','\u{1F64B}','\u{1F647}','\u{1F926}','\u{1F937}','\u{1F486}','\u{1F487}',
'\u{1F6B6}','\u{1F3C3}','\u{1F483}','\u{1F57A}','\u{1F3C7}','\u{1F3C2}','\u{1F3CC}','\u{1F3C4}','\u{1F6A3}','\u{1F3CA}','\u{1F6B4}','\u{1F6B5}',
'\u{1F938}','\u{1F93D}','\u{1F93E}','\u{1F939}','\u{1F9D8}','\u{1F6C0}','\u{1F46E}','\u{1F477}','\u{1F482}','\u{1F385}',
'\u{1F930}','\u{1F931}','\u{1F470}','\u{1F935}','\u{26F7}','\u{26F9}','\u{1F3CB}','\u{1F575}',
];

function esjGetToned(e) {
if (!ESJ.tone) return e;
var base = e.replace(/[\u{1F3FB}-\u{1F3FF}]/gu, '');
if (ESJ_TONE_BASE.indexOf(base) !== -1) {
return base + String.fromCodePoint(parseInt(ESJ.tone, 16));
}
return e;
}

function esjCodePoint(e) {
var cps = [];
for (var i = 0; i < e.length; ) {
var cp = e.codePointAt(i);
cps.push('U+' + cp.toString(16).toUpperCase().padStart(4, '0'));
i += cp > 0xFFFF ? 2 : 1;
}
return cps.join(' ');
}

function esjHtmlEntity(e) {
var parts = [];
for (var i = 0; i < e.length; ) {
var cp = e.codePointAt(i);
parts.push('&#' + cp + ';');
i += cp > 0xFFFF ? 2 : 1;
}
return parts.join('');
}

function esjCssVal(e) {
var parts = [];
for (var i = 0; i < e.length; ) {
var cp = e.codePointAt(i);
parts.push('\\' + cp.toString(16).toUpperCase());
i += cp > 0xFFFF ? 2 : 1;
}
return parts.join(' ');
}

function esjLoadRecent() {
try { ESJ.recent = JSON.parse(localStorage.getItem('esj-recent') || '[]'); } catch(e) { ESJ.recent = []; }
}

function esjSaveRecent(emoji) {
ESJ.recent = [emoji].concat(ESJ.recent.filter(function(x) { return x !== emoji; })).slice(0, 30);
try { localStorage.setItem('esj-recent', JSON.stringify(ESJ.recent)); } catch(e) {}
}

function esjRenderTabs() {
var el = document.getElementById('esj-tabs');
if (!el) return;
el.innerHTML = ESJ_CATS.map(function(c) {
return '<button class="es-tab' + (ESJ.cat === c.id ? ' active' : '') + '" onclick="esjSetTab(this,\'' + c.id + '\')" data-cat="' + c.id + '">' + c.icon + ' ' + c.label + '</button>';
}).join('');
}

function esjFilteredData() {
var q = ESJ.query.trim().toLowerCase();
return ESJ_DATA.filter(function(d) {
if (ESJ.cat !== 'all' && d[2] !== ESJ.cat) return false;
if (q && d[1].indexOf(q) === -1) return false;
return true;
});
}

function esjRender() {
var data = esjFilteredData();
var grid = document.getElementById('esj-grid');
var empty = document.getElementById('esj-empty');
var count = document.getElementById('esj-count');
if (!grid) return;
count.textContent = data.length + '件の絵文字';
if (!data.length) {
grid.innerHTML = '';
empty.style.display = 'block';
return;
}
empty.style.display = 'none';
grid.innerHTML = data.map(function(d) {
var e = esjGetToned(d[0]);
var sel = ESJ.selected && ESJ.selected[0] === d[0];
return '<div class="es-cell' + (sel ? ' selected' : '') + '" onclick="esjSelect(' + JSON.stringify(d[0]) + ',' + JSON.stringify(d[1]) + ')" title="' + d[1] + '">' + e + '</div>';
}).join('');
}

function esjRenderRecent() {
esjLoadRecent();
var box = document.getElementById('esj-recent-box');
var row = document.getElementById('esj-recent-row');
if (!box || !row) return;
if (!ESJ.recent.length) { box.style.display = 'none'; return; }
box.style.display = 'block';
row.innerHTML = ESJ.recent.map(function(e) {
return '<div class="es-cell" onclick="esjSelectByChar(\'' + e + '\')" title="最近使った絵文字">' + esjGetToned(e) + '</div>';
}).join('');
}

function esjShowDetail(e, name) {
var toned = esjGetToned(e);
document.getElementById('esj-preview').textContent = toned;
document.getElementById('esj-info-name').textContent = name.replace(/\b\w/g, function(c) { return c.toUpperCase(); });
document.getElementById('esj-info-cp').textContent = esjCodePoint(toned);
document.getElementById('esj-info-html').textContent = esjHtmlEntity(toned);
document.getElementById('esj-info-css').textContent = esjCssVal(toned);
var det = document.getElementById('esj-detail');
det.classList.add('visible');
}

window.esjSelect = function(e, name) {
ESJ.selected = [e, name];
esjSaveRecent(e);
esjShowDetail(e, name);
esjCopyEmoji(esjGetToned(e));
esjRender();
esjRenderRecent();
};

window.esjSelectByChar = function(e) {
var found = ESJ_DATA.find(function(d) { return d[0] === e; });
var name = found ? found[1] : 'emoji';
ESJ.selected = [e, name];
esjShowDetail(e, name);
esjCopyEmoji(esjGetToned(e));
esjRender();
};

window.esjCopyVal = function(id) {
var el = document.getElementById(id);
if (!el) return;
var txt = el.textContent;
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(txt).then(function() { esjToast('コピーしました: ' + txt); });
} else {
var ta = document.createElement('textarea');
ta.value = txt; ta.style.cssText = 'position:fixed;opacity:0';
document.body.appendChild(ta); ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
esjToast('コピーしました: ' + txt);
}
};

function esjCopyEmoji(e) {
if (navigator.clipboard && navigator.clipboard.writeText) {
navigator.clipboard.writeText(e).then(function() { esjToast('コピーしました! ' + e); });
} else {
var ta = document.createElement('textarea');
ta.value = e; ta.style.cssText = 'position:fixed;opacity:0';
document.body.appendChild(ta); ta.select();
document.execCommand('copy');
document.body.removeChild(ta);
esjToast('コピーしました! ' + e);
}
}

window.esjCopySelected = function() {
if (ESJ.selected) esjCopyEmoji(esjGetToned(ESJ.selected[0]));
};

function esjToast(msg) {
var t = document.getElementById('esj-toast');
t.textContent = msg;
t.classList.add('show');
setTimeout(function() { t.classList.remove('show'); }, 2200);
}

window.esjSearch = function() {
ESJ.query = document.getElementById('es-search').value;
esjRender();
};

window.esjSetTab = function(btn, cat) {
document.querySelectorAll('.es-tab').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
ESJ.cat = cat;
esjRender();
};

window.esjSetTone = function(btn, tone) {
document.querySelectorAll('.es-tone-btn').forEach(function(b) { b.classList.remove('active'); });
btn.classList.add('active');
ESJ.tone = tone;
esjRender();
esjRenderRecent();
if (ESJ.selected) esjShowDetail(ESJ.selected[0], ESJ.selected[1]);
};

esjRenderTabs();
esjRender();
esjRenderRecent();

document.getElementById('es-search').addEventListener('keydown', function(ev) {
if (ev.key === 'Escape') { this.value = ''; ESJ.query = ''; esjRender(); }
});
})();
</script>

</div>

---

**ビジネスの会計・確定申告を効率化しませんか？**

<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freee会計を無料で試す</a>
<img border="0" width="1" height="1" src="https://www10.a8.net/0.gif?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" alt="">

---

関連ツール: Unicode記号を探すなら [Unicode文字マップ](/ja/tools/unicode-character-map/) / ポップアップ形式なら [絵文字ピッカー](/ja/tools/emoji-picker/)
