---
title: "絵文字ピッカー - 無料で絵文字をコピー・検索"
date: 2025-05-16
description: "絵文字をカテゴリー別に検索・コピーできる無料ツール。最近使った絵文字の履歴、スキントーン選択、絵文字情報パネルも搭載。"
categories: ["無料ツール"]
tags: ["絵文字ピッカー", "絵文字コピー", "絵文字検索", "emoji", "無料ツール"]
slug: "emoji-picker"
aliases: ["/ja/tools/emoji-search/", "/ja/tools/emoji-copy/"]
cover:
  image: "/images/covers/emoji-picker-ja.png"
  alt: "絵文字ピッカー"
ShowToc: false
---

<div id="emoji-app">

<style>
#emoji-app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Hiragino Sans', 'Noto Sans JP', Roboto, sans-serif;
  max-width: 900px;
  margin: 0 auto;
  padding: 0 0 40px 0;
  color: #f1f5f9;
}

#emoji-app * {
  box-sizing: border-box;
}

.ep-hero {
  background: linear-gradient(135deg, #78350f 0%, #92400e 40%, #b45309 100%);
  border-radius: 16px;
  padding: 36px 32px;
  margin-bottom: 28px;
  text-align: center;
}

.ep-hero h1 {
  font-size: 2rem;
  font-weight: 800;
  color: #fef9c3;
  margin: 0 0 8px 0;
}

.ep-hero p {
  color: #fde68a;
  margin: 0;
  font-size: 1rem;
}

.ep-controls {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-bottom: 20px;
}

.ep-search-row {
  display: flex;
  gap: 12px;
  align-items: center;
  flex-wrap: wrap;
}

.ep-search {
  flex: 1;
  min-width: 200px;
  padding: 10px 16px;
  border-radius: 10px;
  border: 2px solid #eab308;
  background: #1e293b;
  color: #f1f5f9;
  font-size: 1rem;
  outline: none;
  transition: border-color 0.2s;
}

.ep-search::placeholder {
  color: #64748b;
}

.ep-search:focus {
  border-color: #fbbf24;
}

.ep-tone-label {
  color: #fde68a;
  font-size: 0.85rem;
  font-weight: 600;
  white-space: nowrap;
}

.ep-tone-buttons {
  display: flex;
  gap: 6px;
}

.ep-tone-btn {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  border: 2px solid transparent;
  cursor: pointer;
  font-size: 1.1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #1e293b;
  transition: border-color 0.2s, transform 0.1s;
}

.ep-tone-btn:hover {
  transform: scale(1.15);
}

.ep-tone-btn.active {
  border-color: #eab308;
}

.ep-tabs {
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
  margin-bottom: 16px;
}

.ep-tab {
  padding: 6px 14px;
  border-radius: 20px;
  border: 2px solid #334155;
  background: #1e293b;
  color: #94a3b8;
  cursor: pointer;
  font-size: 0.85rem;
  font-weight: 600;
  transition: all 0.2s;
  white-space: nowrap;
}

.ep-tab:hover {
  border-color: #eab308;
  color: #fde68a;
}

.ep-tab.active {
  background: #eab308;
  border-color: #eab308;
  color: #1e293b;
}

.ep-section-title {
  font-size: 0.8rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #eab308;
  margin: 0 0 10px 0;
}

.ep-recent {
  background: #1e293b;
  border-radius: 12px;
  padding: 14px 16px;
  margin-bottom: 16px;
  border: 1px solid #334155;
}

.ep-recent-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 4px;
}

.ep-grid {
  background: #1e293b;
  border-radius: 12px;
  padding: 14px 16px;
  border: 1px solid #334155;
  margin-bottom: 16px;
}

.ep-emoji-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(44px, 1fr));
  gap: 4px;
}

.ep-emoji-btn {
  width: 44px;
  height: 44px;
  border-radius: 8px;
  border: none;
  background: transparent;
  font-size: 1.5rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.15s, transform 0.1s;
  line-height: 1;
}

.ep-emoji-btn:hover {
  background: #334155;
  transform: scale(1.2);
}

.ep-emoji-btn:active {
  transform: scale(0.95);
}

.ep-info-panel {
  background: #1e293b;
  border-radius: 12px;
  padding: 16px 20px;
  border: 1px solid #eab308;
  margin-bottom: 16px;
  display: none;
}

.ep-info-panel.visible {
  display: block;
}

.ep-info-emoji {
  font-size: 3rem;
  line-height: 1;
  margin-bottom: 10px;
  text-align: center;
}

.ep-info-rows {
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 6px 12px;
  font-size: 0.875rem;
}

.ep-info-label {
  color: #eab308;
  font-weight: 700;
}

.ep-info-value {
  color: #cbd5e1;
  font-family: monospace;
  word-break: break-all;
}

.ep-copy-btn {
  display: block;
  width: 100%;
  margin-top: 12px;
  padding: 10px;
  background: #eab308;
  color: #1e293b;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.2s;
}

.ep-copy-btn:hover {
  background: #fbbf24;
}

.ep-empty {
  text-align: center;
  color: #475569;
  padding: 32px 0;
  font-size: 1rem;
}

.ep-toast {
  position: fixed;
  bottom: 32px;
  left: 50%;
  transform: translateX(-50%) translateY(20px);
  background: #eab308;
  color: #1e293b;
  padding: 10px 24px;
  border-radius: 50px;
  font-weight: 700;
  font-size: 0.95rem;
  opacity: 0;
  transition: opacity 0.3s, transform 0.3s;
  pointer-events: none;
  z-index: 9999;
  white-space: nowrap;
}

.ep-toast.show {
  opacity: 1;
  transform: translateX(-50%) translateY(0);
}

.ep-no-recent {
  color: #475569;
  font-size: 0.85rem;
  font-style: italic;
}

@media (max-width: 600px) {
  .ep-hero h1 { font-size: 1.4rem; }
  .ep-emoji-grid { grid-template-columns: repeat(auto-fill, minmax(40px, 1fr)); }
  .ep-emoji-btn { width: 40px; height: 40px; font-size: 1.3rem; }
}
</style>

<div class="ep-hero">
  <h1>絵文字ピッカー</h1>
  <p>絵文字をクリックするだけでコピー。カテゴリー別・キーワード検索に対応。</p>
</div>

<div class="ep-info-panel" id="ep-info-panel">
  <div class="ep-info-emoji" id="ep-info-emoji"></div>
  <div class="ep-info-rows">
    <span class="ep-info-label">名前</span><span class="ep-info-value" id="ep-info-name"></span>
    <span class="ep-info-label">Unicode</span><span class="ep-info-value" id="ep-info-unicode"></span>
    <span class="ep-info-label">HTML エンティティ</span><span class="ep-info-value" id="ep-info-entity"></span>
    <span class="ep-info-label">カテゴリー</span><span class="ep-info-value" id="ep-info-category"></span>
  </div>
  <button class="ep-copy-btn" id="ep-copy-btn" onclick="epjaCopySelected()">絵文字をコピー</button>
</div>

<div class="ep-controls">
  <div class="ep-search-row">
    <input class="ep-search" id="ep-search" type="text" placeholder="絵文字を検索..." oninput="epjaSearch()" autocomplete="off">
    <span class="ep-tone-label">肌の色:</span>
    <div class="ep-tone-buttons">
      <button class="ep-tone-btn active" data-tone="" onclick="epjaSetTone(this, '')" title="デフォルト">&#x270B;</button>
      <button class="ep-tone-btn" data-tone="\uD83C\uDFFB" onclick="epjaSetTone(this, '\uD83C\uDFFB')" title="明るい" style="filter:sepia(1) saturate(3) hue-rotate(340deg);">&#x270B;</button>
      <button class="ep-tone-btn" data-tone="\uD83C\uDFFC" onclick="epjaSetTone(this, '\uD83C\uDFFC')" title="やや明るい" style="filter:sepia(1) saturate(2) hue-rotate(10deg);">&#x270B;</button>
      <button class="ep-tone-btn" data-tone="\uD83C\uDFFD" onclick="epjaSetTone(this, '\uD83C\uDFFD')" title="中間" style="filter:sepia(1) saturate(2) hue-rotate(350deg) brightness(0.85);">&#x270B;</button>
      <button class="ep-tone-btn" data-tone="\uD83C\uDFFE" onclick="epjaSetTone(this, '\uD83C\uDFFE')" title="やや暗い" style="filter:sepia(1) saturate(2) hue-rotate(350deg) brightness(0.65);">&#x270B;</button>
    </div>
  </div>
</div>

<div class="ep-tabs" id="ep-tabs">
  <button class="ep-tab active" data-cat="all" onclick="epjaSetTab(this)">すべて</button>
  <button class="ep-tab" data-cat="Smileys" onclick="epjaSetTab(this)">顔・表情</button>
  <button class="ep-tab" data-cat="People" onclick="epjaSetTab(this)">人・体</button>
  <button class="ep-tab" data-cat="Animals" onclick="epjaSetTab(this)">動物・自然</button>
  <button class="ep-tab" data-cat="Food" onclick="epjaSetTab(this)">食べ物・飲み物</button>
  <button class="ep-tab" data-cat="Travel" onclick="epjaSetTab(this)">旅行・乗り物</button>
  <button class="ep-tab" data-cat="Objects" onclick="epjaSetTab(this)">物・道具</button>
  <button class="ep-tab" data-cat="Symbols" onclick="epjaSetTab(this)">記号・マーク</button>
  <button class="ep-tab" data-cat="Flags" onclick="epjaSetTab(this)">旗</button>
</div>

<div class="ep-recent" id="ep-recent-section">
  <div class="ep-section-title">最近使った絵文字</div>
  <div class="ep-recent-grid" id="ep-recent-grid">
    <span class="ep-no-recent">まだ使った絵文字はありません</span>
  </div>
</div>

<div class="ep-grid">
  <div class="ep-section-title" id="ep-grid-title">すべての絵文字</div>
  <div class="ep-emoji-grid" id="ep-emoji-grid"></div>
</div>

<div class="ep-toast" id="ep-toast"></div>

<script>
(function() {
  var EPJ = {
    tone: '',
    cat: 'all',
    query: '',
    selected: null,
    catLabel: {
      'all':'すべて','Smileys':'顔・表情','People':'人・体',
      'Animals':'動物・自然','Food':'食べ物・飲み物','Travel':'旅行・乗り物',
      'Objects':'物・道具','Symbols':'記号・マーク','Flags':'旗'
    },
    data: [
      // Smileys
      {e:'😀',n:'Grinning Face',c:'Smileys'},{e:'😁',n:'Beaming Face',c:'Smileys'},
      {e:'😂',n:'Face with Tears of Joy',c:'Smileys'},{e:'🤣',n:'Rolling on Floor Laughing',c:'Smileys'},
      {e:'😃',n:'Grinning Face with Big Eyes',c:'Smileys'},{e:'😄',n:'Grinning Face with Smiling Eyes',c:'Smileys'},
      {e:'😅',n:'Grinning Face with Sweat',c:'Smileys'},{e:'😆',n:'Squinting Face with Joy',c:'Smileys'},
      {e:'😉',n:'Winking Face',c:'Smileys'},{e:'😊',n:'Smiling Face with Smiling Eyes',c:'Smileys'},
      {e:'😋',n:'Face Savoring Food',c:'Smileys'},{e:'😎',n:'Smiling Face with Sunglasses',c:'Smileys'},
      {e:'😍',n:'Smiling Face with Heart-Eyes',c:'Smileys'},{e:'🥰',n:'Smiling Face with Hearts',c:'Smileys'},
      {e:'😘',n:'Face Blowing a Kiss',c:'Smileys'},{e:'😗',n:'Kissing Face',c:'Smileys'},
      {e:'🤩',n:'Star-Struck',c:'Smileys'},{e:'🥳',n:'Partying Face',c:'Smileys'},
      {e:'😏',n:'Smirking Face',c:'Smileys'},{e:'😒',n:'Unamused Face',c:'Smileys'},
      {e:'😞',n:'Disappointed Face',c:'Smileys'},{e:'😔',n:'Pensive Face',c:'Smileys'},
      {e:'😟',n:'Worried Face',c:'Smileys'},{e:'😕',n:'Confused Face',c:'Smileys'},
      {e:'🙁',n:'Slightly Frowning Face',c:'Smileys'},{e:'😣',n:'Persevering Face',c:'Smileys'},
      {e:'😖',n:'Confounded Face',c:'Smileys'},{e:'😫',n:'Tired Face',c:'Smileys'},
      {e:'😩',n:'Weary Face',c:'Smileys'},{e:'🥺',n:'Pleading Face',c:'Smileys'},
      {e:'😢',n:'Crying Face',c:'Smileys'},{e:'😭',n:'Loudly Crying Face',c:'Smileys'},
      {e:'😤',n:'Face with Steam from Nose',c:'Smileys'},{e:'😠',n:'Angry Face',c:'Smileys'},
      {e:'😡',n:'Enraged Face',c:'Smileys'},{e:'🤬',n:'Face with Symbols on Mouth',c:'Smileys'},
      {e:'🤯',n:'Exploding Head',c:'Smileys'},{e:'😳',n:'Flushed Face',c:'Smileys'},
      {e:'🥵',n:'Hot Face',c:'Smileys'},{e:'🥶',n:'Cold Face',c:'Smileys'},
      {e:'😱',n:'Face Screaming in Fear',c:'Smileys'},{e:'😨',n:'Fearful Face',c:'Smileys'},
      {e:'😰',n:'Anxious Face with Sweat',c:'Smileys'},{e:'😥',n:'Sad but Relieved Face',c:'Smileys'},
      {e:'😓',n:'Downcast Face with Sweat',c:'Smileys'},{e:'🤫',n:'Shushing Face',c:'Smileys'},
      {e:'🤔',n:'Thinking Face',c:'Smileys'},{e:'🤭',n:'Face with Hand Over Mouth',c:'Smileys'},
      {e:'🤗',n:'Hugging Face',c:'Smileys'},{e:'🤥',n:'Lying Face',c:'Smileys'},
      {e:'😶',n:'Face Without Mouth',c:'Smileys'},{e:'😐',n:'Neutral Face',c:'Smileys'},
      {e:'😑',n:'Expressionless Face',c:'Smileys'},{e:'😬',n:'Grimacing Face',c:'Smileys'},
      {e:'🙄',n:'Face with Rolling Eyes',c:'Smileys'},{e:'😯',n:'Hushed Face',c:'Smileys'},
      {e:'😦',n:'Frowning Face with Open Mouth',c:'Smileys'},{e:'😧',n:'Anguished Face',c:'Smileys'},
      {e:'😮',n:'Face with Open Mouth',c:'Smileys'},{e:'😲',n:'Astonished Face',c:'Smileys'},
      {e:'🥱',n:'Yawning Face',c:'Smileys'},{e:'😴',n:'Sleeping Face',c:'Smileys'},
      {e:'🤤',n:'Drooling Face',c:'Smileys'},{e:'😪',n:'Sleepy Face',c:'Smileys'},
      {e:'😵',n:'Dizzy Face',c:'Smileys'},{e:'🤐',n:'Zipper-Mouth Face',c:'Smileys'},
      {e:'🥴',n:'Woozy Face',c:'Smileys'},{e:'🤢',n:'Nauseated Face',c:'Smileys'},
      {e:'🤮',n:'Face Vomiting',c:'Smileys'},{e:'🤧',n:'Sneezing Face',c:'Smileys'},
      {e:'😷',n:'Face with Medical Mask',c:'Smileys'},{e:'🤒',n:'Face with Thermometer',c:'Smileys'},
      {e:'🤕',n:'Face with Head-Bandage',c:'Smileys'},{e:'🤑',n:'Money-Mouth Face',c:'Smileys'},
      {e:'😈',n:'Smiling Face with Horns',c:'Smileys'},{e:'👿',n:'Angry Face with Horns',c:'Smileys'},
      {e:'💀',n:'Skull',c:'Smileys'},{e:'☠️',n:'Skull and Crossbones',c:'Smileys'},
      {e:'👻',n:'Ghost',c:'Smileys'},{e:'👽',n:'Alien',c:'Smileys'},
      {e:'🤖',n:'Robot',c:'Smileys'},{e:'💩',n:'Pile of Poo',c:'Smileys'},
      {e:'😺',n:'Grinning Cat',c:'Smileys'},{e:'😸',n:'Grinning Cat with Smiling Eyes',c:'Smileys'},
      {e:'😹',n:'Cat with Tears of Joy',c:'Smileys'},{e:'😻',n:'Smiling Cat with Heart-Eyes',c:'Smileys'},
      // People
      {e:'👋',n:'Waving Hand',c:'People'},{e:'🤚',n:'Raised Back of Hand',c:'People'},
      {e:'✋',n:'Raised Hand',c:'People'},{e:'🖖',n:'Vulcan Salute',c:'People'},
      {e:'👌',n:'OK Hand',c:'People'},{e:'🤌',n:'Pinched Fingers',c:'People'},
      {e:'✌️',n:'Victory Hand',c:'People'},{e:'🤞',n:'Crossed Fingers',c:'People'},
      {e:'🤟',n:'Love-You Gesture',c:'People'},{e:'🤘',n:'Sign of the Horns',c:'People'},
      {e:'👈',n:'Backhand Index Pointing Left',c:'People'},{e:'👉',n:'Backhand Index Pointing Right',c:'People'},
      {e:'👆',n:'Backhand Index Pointing Up',c:'People'},{e:'👇',n:'Backhand Index Pointing Down',c:'People'},
      {e:'☝️',n:'Index Pointing Up',c:'People'},{e:'👍',n:'Thumbs Up',c:'People'},
      {e:'👎',n:'Thumbs Down',c:'People'},{e:'✊',n:'Raised Fist',c:'People'},
      {e:'👊',n:'Oncoming Fist',c:'People'},{e:'🤛',n:'Left-Facing Fist',c:'People'},
      {e:'🤜',n:'Right-Facing Fist',c:'People'},{e:'👏',n:'Clapping Hands',c:'People'},
      {e:'🙌',n:'Raising Hands',c:'People'},{e:'👐',n:'Open Hands',c:'People'},
      {e:'🤲',n:'Palms Up Together',c:'People'},{e:'🙏',n:'Folded Hands',c:'People'},
      {e:'✍️',n:'Writing Hand',c:'People'},{e:'💅',n:'Nail Polish',c:'People'},
      {e:'🤳',n:'Selfie',c:'People'},{e:'💪',n:'Flexed Biceps',c:'People'},
      {e:'🦵',n:'Leg',c:'People'},{e:'🦶',n:'Foot',c:'People'},
      {e:'👂',n:'Ear',c:'People'},{e:'👃',n:'Nose',c:'People'},
      {e:'🧠',n:'Brain',c:'People'},{e:'👁️',n:'Eye',c:'People'},
      {e:'👅',n:'Tongue',c:'People'},{e:'👄',n:'Mouth',c:'People'},
      {e:'👶',n:'Baby',c:'People'},{e:'🧒',n:'Child',c:'People'},
      {e:'👦',n:'Boy',c:'People'},{e:'👧',n:'Girl',c:'People'},
      {e:'🧑',n:'Person',c:'People'},{e:'👱',n:'Person Blond Hair',c:'People'},
      {e:'👨',n:'Man',c:'People'},{e:'👩',n:'Woman',c:'People'},
      {e:'🧓',n:'Older Person',c:'People'},{e:'👴',n:'Old Man',c:'People'},
      {e:'👵',n:'Old Woman',c:'People'},{e:'🙍',n:'Person Frowning',c:'People'},
      {e:'🙎',n:'Person Pouting',c:'People'},{e:'🙅',n:'Person Gesturing No',c:'People'},
      {e:'🙆',n:'Person Gesturing OK',c:'People'},{e:'💁',n:'Person Tipping Hand',c:'People'},
      {e:'🙋',n:'Person Raising Hand',c:'People'},{e:'🧏',n:'Deaf Person',c:'People'},
      {e:'🙇',n:'Person Bowing',c:'People'},{e:'🤦',n:'Person Facepalming',c:'People'},
      {e:'🤷',n:'Person Shrugging',c:'People'},{e:'👮',n:'Police Officer',c:'People'},
      {e:'🕵️',n:'Detective',c:'People'},{e:'💂',n:'Guard',c:'People'},
      {e:'👷',n:'Construction Worker',c:'People'},{e:'🤴',n:'Prince',c:'People'},
      {e:'👸',n:'Princess',c:'People'},{e:'👳',n:'Person Wearing Turban',c:'People'},
      {e:'👲',n:'Person with Skullcap',c:'People'},{e:'🧕',n:'Woman with Headscarf',c:'People'},
      // Animals
      {e:'🐶',n:'Dog Face',c:'Animals'},{e:'🐱',n:'Cat Face',c:'Animals'},
      {e:'🐭',n:'Mouse Face',c:'Animals'},{e:'🐹',n:'Hamster',c:'Animals'},
      {e:'🐰',n:'Rabbit Face',c:'Animals'},{e:'🦊',n:'Fox',c:'Animals'},
      {e:'🐻',n:'Bear',c:'Animals'},{e:'🐼',n:'Panda',c:'Animals'},
      {e:'🐨',n:'Koala',c:'Animals'},{e:'🐯',n:'Tiger Face',c:'Animals'},
      {e:'🦁',n:'Lion',c:'Animals'},{e:'🐮',n:'Cow Face',c:'Animals'},
      {e:'🐷',n:'Pig Face',c:'Animals'},{e:'🐸',n:'Frog',c:'Animals'},
      {e:'🐵',n:'Monkey Face',c:'Animals'},{e:'🙈',n:'See-No-Evil Monkey',c:'Animals'},
      {e:'🙉',n:'Hear-No-Evil Monkey',c:'Animals'},{e:'🙊',n:'Speak-No-Evil Monkey',c:'Animals'},
      {e:'🐔',n:'Chicken',c:'Animals'},{e:'🐧',n:'Penguin',c:'Animals'},
      {e:'🐦',n:'Bird',c:'Animals'},{e:'🦆',n:'Duck',c:'Animals'},
      {e:'🦅',n:'Eagle',c:'Animals'},{e:'🦉',n:'Owl',c:'Animals'},
      {e:'🦇',n:'Bat',c:'Animals'},{e:'🐺',n:'Wolf',c:'Animals'},
      {e:'🐗',n:'Boar',c:'Animals'},{e:'🐴',n:'Horse Face',c:'Animals'},
      {e:'🦄',n:'Unicorn',c:'Animals'},{e:'🐝',n:'Honeybee',c:'Animals'},
      {e:'🐛',n:'Bug',c:'Animals'},{e:'🦋',n:'Butterfly',c:'Animals'},
      {e:'🐌',n:'Snail',c:'Animals'},{e:'🐞',n:'Lady Beetle',c:'Animals'},
      {e:'🐜',n:'Ant',c:'Animals'},{e:'🦟',n:'Mosquito',c:'Animals'},
      {e:'🦗',n:'Cricket',c:'Animals'},{e:'🕷️',n:'Spider',c:'Animals'},
      {e:'🐢',n:'Turtle',c:'Animals'},{e:'🐍',n:'Snake',c:'Animals'},
      {e:'🦎',n:'Lizard',c:'Animals'},{e:'🐊',n:'Crocodile',c:'Animals'},
      {e:'🦕',n:'Sauropod',c:'Animals'},{e:'🦖',n:'T-Rex',c:'Animals'},
      {e:'🐳',n:'Spouting Whale',c:'Animals'},{e:'🐋',n:'Whale',c:'Animals'},
      {e:'🦈',n:'Shark',c:'Animals'},{e:'🐬',n:'Dolphin',c:'Animals'},
      {e:'🐟',n:'Fish',c:'Animals'},{e:'🐠',n:'Tropical Fish',c:'Animals'},
      {e:'🐡',n:'Blowfish',c:'Animals'},{e:'🦑',n:'Squid',c:'Animals'},
      {e:'🐙',n:'Octopus',c:'Animals'},{e:'🦐',n:'Shrimp',c:'Animals'},
      {e:'🦞',n:'Lobster',c:'Animals'},{e:'🦀',n:'Crab',c:'Animals'},
      {e:'🐅',n:'Tiger',c:'Animals'},{e:'🐆',n:'Leopard',c:'Animals'},
      {e:'🦒',n:'Giraffe',c:'Animals'},{e:'🦘',n:'Kangaroo',c:'Animals'},
      {e:'🦛',n:'Hippopotamus',c:'Animals'},{e:'🐘',n:'Elephant',c:'Animals'},
      {e:'🦏',n:'Rhinoceros',c:'Animals'},{e:'🐪',n:'Camel',c:'Animals'},
      {e:'🦙',n:'Llama',c:'Animals'},{e:'🦓',n:'Zebra',c:'Animals'},
      {e:'🦍',n:'Gorilla',c:'Animals'},{e:'🦧',n:'Orangutan',c:'Animals'},
      // Food
      {e:'🍎',n:'Red Apple',c:'Food'},{e:'🍊',n:'Tangerine',c:'Food'},
      {e:'🍋',n:'Lemon',c:'Food'},{e:'🍇',n:'Grapes',c:'Food'},
      {e:'🍓',n:'Strawberry',c:'Food'},{e:'🫐',n:'Blueberries',c:'Food'},
      {e:'🍈',n:'Melon',c:'Food'},{e:'🍉',n:'Watermelon',c:'Food'},
      {e:'🍌',n:'Banana',c:'Food'},{e:'🍍',n:'Pineapple',c:'Food'},
      {e:'🥭',n:'Mango',c:'Food'},{e:'🍑',n:'Peach',c:'Food'},
      {e:'🍒',n:'Cherries',c:'Food'},{e:'🍐',n:'Pear',c:'Food'},
      {e:'🥝',n:'Kiwi Fruit',c:'Food'},{e:'🍅',n:'Tomato',c:'Food'},
      {e:'🫒',n:'Olive',c:'Food'},{e:'🥥',n:'Coconut',c:'Food'},
      {e:'🥑',n:'Avocado',c:'Food'},{e:'🍆',n:'Eggplant',c:'Food'},
      {e:'🥔',n:'Potato',c:'Food'},{e:'🥕',n:'Carrot',c:'Food'},
      {e:'🌽',n:'Ear of Corn',c:'Food'},{e:'🌶️',n:'Hot Pepper',c:'Food'},
      {e:'🥦',n:'Broccoli',c:'Food'},{e:'🧅',n:'Onion',c:'Food'},
      {e:'🍄',n:'Mushroom',c:'Food'},{e:'🥜',n:'Peanuts',c:'Food'},
      {e:'🍞',n:'Bread',c:'Food'},{e:'🥐',n:'Croissant',c:'Food'},
      {e:'🥖',n:'Baguette Bread',c:'Food'},{e:'🫓',n:'Flatbread',c:'Food'},
      {e:'🧀',n:'Cheese Wedge',c:'Food'},{e:'🥚',n:'Egg',c:'Food'},
      {e:'🍳',n:'Cooking',c:'Food'},{e:'🧈',n:'Butter',c:'Food'},
      {e:'🥞',n:'Pancakes',c:'Food'},{e:'🧇',n:'Waffle',c:'Food'},
      {e:'🥓',n:'Bacon',c:'Food'},{e:'🥩',n:'Cut of Meat',c:'Food'},
      {e:'🍗',n:'Poultry Leg',c:'Food'},{e:'🍖',n:'Meat on Bone',c:'Food'},
      {e:'🌭',n:'Hot Dog',c:'Food'},{e:'🍔',n:'Hamburger',c:'Food'},
      {e:'🍟',n:'French Fries',c:'Food'},{e:'🍕',n:'Pizza',c:'Food'},
      {e:'🫔',n:'Tamale',c:'Food'},{e:'🥙',n:'Stuffed Flatbread',c:'Food'},
      {e:'🍜',n:'Steaming Bowl',c:'Food'},{e:'🍝',n:'Spaghetti',c:'Food'},
      {e:'🍛',n:'Curry Rice',c:'Food'},{e:'🍣',n:'Sushi',c:'Food'},
      {e:'🍱',n:'Bento Box',c:'Food'},{e:'🍤',n:'Fried Shrimp',c:'Food'},
      {e:'🍙',n:'Rice Ball',c:'Food'},{e:'🍚',n:'Cooked Rice',c:'Food'},
      {e:'🍘',n:'Rice Cracker',c:'Food'},{e:'🍥',n:'Fish Cake with Swirl',c:'Food'},
      {e:'🍦',n:'Soft Ice Cream',c:'Food'},{e:'🍧',n:'Shaved Ice',c:'Food'},
      {e:'🍨',n:'Ice Cream',c:'Food'},{e:'🍩',n:'Doughnut',c:'Food'},
      {e:'🍪',n:'Cookie',c:'Food'},{e:'🎂',n:'Birthday Cake',c:'Food'},
      {e:'🍰',n:'Shortcake',c:'Food'},{e:'🧁',n:'Cupcake',c:'Food'},
      {e:'🥧',n:'Pie',c:'Food'},{e:'🍫',n:'Chocolate Bar',c:'Food'},
      {e:'🍬',n:'Candy',c:'Food'},{e:'🍭',n:'Lollipop',c:'Food'},
      {e:'☕',n:'Hot Beverage',c:'Food'},{e:'🍵',n:'Teacup Without Handle',c:'Food'},
      {e:'🧃',n:'Beverage Box',c:'Food'},{e:'🥤',n:'Cup with Straw',c:'Food'},
      {e:'🍺',n:'Beer Mug',c:'Food'},{e:'🍻',n:'Clinking Beer Mugs',c:'Food'},
      {e:'🥂',n:'Clinking Glasses',c:'Food'},{e:'🍷',n:'Wine Glass',c:'Food'},
      {e:'🍸',n:'Cocktail Glass',c:'Food'},{e:'🍹',n:'Tropical Drink',c:'Food'},
      // Travel
      {e:'🚗',n:'Automobile',c:'Travel'},{e:'🚕',n:'Taxi',c:'Travel'},
      {e:'🚙',n:'Sport Utility Vehicle',c:'Travel'},{e:'🚌',n:'Bus',c:'Travel'},
      {e:'🚎',n:'Trolleybus',c:'Travel'},{e:'🏎️',n:'Racing Car',c:'Travel'},
      {e:'🚓',n:'Police Car',c:'Travel'},{e:'🚑',n:'Ambulance',c:'Travel'},
      {e:'🚒',n:'Fire Engine',c:'Travel'},{e:'🚐',n:'Minibus',c:'Travel'},
      {e:'🚚',n:'Delivery Truck',c:'Travel'},{e:'✈️',n:'Airplane',c:'Travel'},
      {e:'🚀',n:'Rocket',c:'Travel'},{e:'🛸',n:'Flying Saucer',c:'Travel'},
      {e:'🚁',n:'Helicopter',c:'Travel'},{e:'🛶',n:'Canoe',c:'Travel'},
      {e:'⛵',n:'Sailboat',c:'Travel'},{e:'🚢',n:'Ship',c:'Travel'},
      {e:'🚂',n:'Locomotive',c:'Travel'},{e:'🚃',n:'Railway Car',c:'Travel'},
      {e:'🚆',n:'Train',c:'Travel'},{e:'🚇',n:'Metro',c:'Travel'},
      {e:'🚈',n:'Light Rail',c:'Travel'},{e:'🚉',n:'Station',c:'Travel'},
      {e:'🚊',n:'Tram',c:'Travel'},{e:'🏍️',n:'Motorcycle',c:'Travel'},
      {e:'🛵',n:'Motor Scooter',c:'Travel'},{e:'🚲',n:'Bicycle',c:'Travel'},
      {e:'🛴',n:'Kick Scooter',c:'Travel'},{e:'🛺',n:'Auto Rickshaw',c:'Travel'},
      {e:'🏖️',n:'Beach with Umbrella',c:'Travel'},{e:'🏔️',n:'Snow-Capped Mountain',c:'Travel'},
      {e:'🗻',n:'Mount Fuji',c:'Travel'},{e:'🏕️',n:'Camping',c:'Travel'},
      {e:'🏜️',n:'Desert',c:'Travel'},{e:'🏝️',n:'Desert Island',c:'Travel'},
      {e:'🌋',n:'Volcano',c:'Travel'},{e:'🗼',n:'Tokyo Tower',c:'Travel'},
      {e:'🗽',n:'Statue of Liberty',c:'Travel'},{e:'🗿',n:'Moai',c:'Travel'},
      {e:'🏰',n:'Castle',c:'Travel'},{e:'🏯',n:'Japanese Castle',c:'Travel'},
      {e:'🌏',n:'Globe Showing Asia-Australia',c:'Travel'},{e:'🌍',n:'Globe Showing Europe-Africa',c:'Travel'},
      {e:'🌎',n:'Globe Showing Americas',c:'Travel'},{e:'🗺️',n:'World Map',c:'Travel'},
      {e:'🧭',n:'Compass',c:'Travel'},{e:'🌐',n:'Globe with Meridians',c:'Travel'},
      // Objects
      {e:'⌚',n:'Watch',c:'Objects'},{e:'📱',n:'Mobile Phone',c:'Objects'},
      {e:'💻',n:'Laptop',c:'Objects'},{e:'⌨️',n:'Keyboard',c:'Objects'},
      {e:'🖥️',n:'Desktop Computer',c:'Objects'},{e:'🖨️',n:'Printer',c:'Objects'},
      {e:'🖱️',n:'Computer Mouse',c:'Objects'},{e:'💾',n:'Floppy Disk',c:'Objects'},
      {e:'💿',n:'Optical Disk',c:'Objects'},{e:'📀',n:'DVD',c:'Objects'},
      {e:'📷',n:'Camera',c:'Objects'},{e:'📸',n:'Camera with Flash',c:'Objects'},
      {e:'📹',n:'Video Camera',c:'Objects'},{e:'📼',n:'Videocassette',c:'Objects'},
      {e:'📞',n:'Telephone Receiver',c:'Objects'},{e:'☎️',n:'Telephone',c:'Objects'},
      {e:'📟',n:'Pager',c:'Objects'},{e:'📠',n:'Fax Machine',c:'Objects'},
      {e:'📺',n:'Television',c:'Objects'},{e:'📻',n:'Radio',c:'Objects'},
      {e:'⏰',n:'Alarm Clock',c:'Objects'},{e:'💡',n:'Light Bulb',c:'Objects'},
      {e:'🔦',n:'Flashlight',c:'Objects'},{e:'🕯️',n:'Candle',c:'Objects'},
      {e:'🔋',n:'Battery',c:'Objects'},{e:'🔌',n:'Electric Plug',c:'Objects'},
      {e:'🛒',n:'Shopping Cart',c:'Objects'},{e:'💊',n:'Pill',c:'Objects'},
      {e:'💉',n:'Syringe',c:'Objects'},{e:'🩺',n:'Stethoscope',c:'Objects'},
      {e:'🔬',n:'Microscope',c:'Objects'},{e:'🔭',n:'Telescope',c:'Objects'},
      {e:'📚',n:'Books',c:'Objects'},{e:'📖',n:'Open Book',c:'Objects'},
      {e:'📝',n:'Memo',c:'Objects'},{e:'📄',n:'Page Facing Up',c:'Objects'},
      {e:'✏️',n:'Pencil',c:'Objects'},{e:'🖊️',n:'Pen',c:'Objects'},
      {e:'🖋️',n:'Fountain Pen',c:'Objects'},{e:'🗑️',n:'Wastebasket',c:'Objects'},
      {e:'💼',n:'Briefcase',c:'Objects'},{e:'👜',n:'Handbag',c:'Objects'},
      {e:'👛',n:'Purse',c:'Objects'},{e:'🎒',n:'Backpack',c:'Objects'},
      {e:'🧳',n:'Luggage',c:'Objects'},{e:'🔑',n:'Key',c:'Objects'},
      {e:'🗝️',n:'Old Key',c:'Objects'},{e:'🔒',n:'Locked',c:'Objects'},
      {e:'🔓',n:'Unlocked',c:'Objects'},{e:'🔨',n:'Hammer',c:'Objects'},
      {e:'⚙️',n:'Gear',c:'Objects'},{e:'🔧',n:'Wrench',c:'Objects'},
      {e:'🔩',n:'Nut and Bolt',c:'Objects'},{e:'🧲',n:'Magnet',c:'Objects'},
      {e:'🎈',n:'Balloon',c:'Objects'},{e:'🎉',n:'Party Popper',c:'Objects'},
      {e:'🎊',n:'Confetti Ball',c:'Objects'},{e:'🎁',n:'Wrapped Gift',c:'Objects'},
      {e:'🏆',n:'Trophy',c:'Objects'},{e:'🥇',n:'1st Place Medal',c:'Objects'},
      {e:'🥈',n:'2nd Place Medal',c:'Objects'},{e:'🥉',n:'3rd Place Medal',c:'Objects'},
      // Symbols
      {e:'❤️',n:'Red Heart',c:'Symbols'},{e:'🧡',n:'Orange Heart',c:'Symbols'},
      {e:'💛',n:'Yellow Heart',c:'Symbols'},{e:'💚',n:'Green Heart',c:'Symbols'},
      {e:'💙',n:'Blue Heart',c:'Symbols'},{e:'💜',n:'Purple Heart',c:'Symbols'},
      {e:'🖤',n:'Black Heart',c:'Symbols'},{e:'🤍',n:'White Heart',c:'Symbols'},
      {e:'🤎',n:'Brown Heart',c:'Symbols'},{e:'💔',n:'Broken Heart',c:'Symbols'},
      {e:'❣️',n:'Heart Exclamation',c:'Symbols'},{e:'💕',n:'Two Hearts',c:'Symbols'},
      {e:'💞',n:'Revolving Hearts',c:'Symbols'},{e:'💓',n:'Beating Heart',c:'Symbols'},
      {e:'💗',n:'Growing Heart',c:'Symbols'},{e:'💖',n:'Sparkling Heart',c:'Symbols'},
      {e:'💘',n:'Heart with Arrow',c:'Symbols'},{e:'💝',n:'Heart with Ribbon',c:'Symbols'},
      {e:'☮️',n:'Peace Symbol',c:'Symbols'},{e:'☯️',n:'Yin Yang',c:'Symbols'},
      {e:'♻️',n:'Recycling Symbol',c:'Symbols'},{e:'✅',n:'Check Mark Button',c:'Symbols'},
      {e:'❌',n:'Cross Mark',c:'Symbols'},{e:'❎',n:'Cross Mark Button',c:'Symbols'},
      {e:'⭕',n:'Hollow Red Circle',c:'Symbols'},{e:'🔴',n:'Red Circle',c:'Symbols'},
      {e:'🟠',n:'Orange Circle',c:'Symbols'},{e:'🟡',n:'Yellow Circle',c:'Symbols'},
      {e:'🟢',n:'Green Circle',c:'Symbols'},{e:'🔵',n:'Blue Circle',c:'Symbols'},
      {e:'🟣',n:'Purple Circle',c:'Symbols'},{e:'⚫',n:'Black Circle',c:'Symbols'},
      {e:'⚪',n:'White Circle',c:'Symbols'},{e:'⭐',n:'Star',c:'Symbols'},
      {e:'🌟',n:'Glowing Star',c:'Symbols'},{e:'💫',n:'Dizzy',c:'Symbols'},
      {e:'✨',n:'Sparkles',c:'Symbols'},{e:'🌈',n:'Rainbow',c:'Symbols'},
      {e:'☀️',n:'Sun',c:'Symbols'},{e:'🌙',n:'Crescent Moon',c:'Symbols'},
      {e:'⚡',n:'High Voltage',c:'Symbols'},{e:'❄️',n:'Snowflake',c:'Symbols'},
      {e:'🔥',n:'Fire',c:'Symbols'},{e:'💧',n:'Droplet',c:'Symbols'},
      {e:'🌊',n:'Water Wave',c:'Symbols'},{e:'🎵',n:'Musical Note',c:'Symbols'},
      {e:'🎶',n:'Musical Notes',c:'Symbols'},{e:'💯',n:'Hundred Points',c:'Symbols'},
      {e:'🔔',n:'Bell',c:'Symbols'},{e:'📣',n:'Megaphone',c:'Symbols'},
      {e:'📢',n:'Loudspeaker',c:'Symbols'},{e:'🔊',n:'Speaker High Volume',c:'Symbols'},
      {e:'💬',n:'Speech Balloon',c:'Symbols'},{e:'💭',n:'Thought Balloon',c:'Symbols'},
      {e:'🔗',n:'Link',c:'Symbols'},{e:'📌',n:'Pushpin',c:'Symbols'},
      {e:'✂️',n:'Scissors',c:'Symbols'},{e:'📅',n:'Calendar',c:'Symbols'},
      {e:'⏳',n:'Hourglass Not Done',c:'Symbols'},{e:'⌛',n:'Hourglass Done',c:'Symbols'},
      {e:'🚫',n:'Prohibited',c:'Symbols'},{e:'⚠️',n:'Warning',c:'Symbols'},
      {e:'♿',n:'Wheelchair Symbol',c:'Symbols'},{e:'🆘',n:'SOS Button',c:'Symbols'},
      {e:'🆗',n:'OK Button',c:'Symbols'},{e:'🆕',n:'NEW Button',c:'Symbols'},
      {e:'🆓',n:'FREE Button',c:'Symbols'},
      // Flags
      {e:'🏳️',n:'White Flag',c:'Flags'},{e:'🏴',n:'Black Flag',c:'Flags'},
      {e:'🚩',n:'Triangular Flag',c:'Flags'},{e:'🏁',n:'Chequered Flag',c:'Flags'},
      {e:'🏳️‍🌈',n:'Rainbow Flag',c:'Flags'},{e:'🏳️‍⚧️',n:'Transgender Flag',c:'Flags'},
      {e:'🇺🇸',n:'Flag: United States',c:'Flags'},{e:'🇬🇧',n:'Flag: United Kingdom',c:'Flags'},
      {e:'🇨🇦',n:'Flag: Canada',c:'Flags'},{e:'🇦🇺',n:'Flag: Australia',c:'Flags'},
      {e:'🇯🇵',n:'Flag: Japan',c:'Flags'},{e:'🇰🇷',n:'Flag: South Korea',c:'Flags'},
      {e:'🇨🇳',n:'Flag: China',c:'Flags'},{e:'🇮🇳',n:'Flag: India',c:'Flags'},
      {e:'🇧🇷',n:'Flag: Brazil',c:'Flags'},{e:'🇲🇽',n:'Flag: Mexico',c:'Flags'},
      {e:'🇩🇪',n:'Flag: Germany',c:'Flags'},{e:'🇫🇷',n:'Flag: France',c:'Flags'},
      {e:'🇮🇹',n:'Flag: Italy',c:'Flags'},{e:'🇪🇸',n:'Flag: Spain',c:'Flags'},
      {e:'🇵🇹',n:'Flag: Portugal',c:'Flags'},{e:'🇷🇺',n:'Flag: Russia',c:'Flags'},
      {e:'🇸🇦',n:'Flag: Saudi Arabia',c:'Flags'},{e:'🇿🇦',n:'Flag: South Africa',c:'Flags'},
      {e:'🇳🇬',n:'Flag: Nigeria',c:'Flags'},{e:'🇦🇷',n:'Flag: Argentina',c:'Flags'},
      {e:'🇸🇪',n:'Flag: Sweden',c:'Flags'},{e:'🇳🇴',n:'Flag: Norway',c:'Flags'},
      {e:'🇩🇰',n:'Flag: Denmark',c:'Flags'},{e:'🇫🇮',n:'Flag: Finland',c:'Flags'},
      {e:'🇳🇱',n:'Flag: Netherlands',c:'Flags'},{e:'🇧🇪',n:'Flag: Belgium',c:'Flags'},
      {e:'🇨🇭',n:'Flag: Switzerland',c:'Flags'},{e:'🇦🇹',n:'Flag: Austria',c:'Flags'},
      {e:'🇵🇱',n:'Flag: Poland',c:'Flags'},{e:'🇬🇷',n:'Flag: Greece',c:'Flags'},
      {e:'🇹🇷',n:'Flag: Turkey',c:'Flags'},{e:'🇮🇩',n:'Flag: Indonesia',c:'Flags'},
      {e:'🇹🇭',n:'Flag: Thailand',c:'Flags'},{e:'🇻🇳',n:'Flag: Vietnam',c:'Flags'},
      {e:'🇵🇭',n:'Flag: Philippines',c:'Flags'},{e:'🇲🇾',n:'Flag: Malaysia',c:'Flags'},
      {e:'🇸🇬',n:'Flag: Singapore',c:'Flags'},{e:'🇳🇿',n:'Flag: New Zealand',c:'Flags'},
      {e:'🇺🇦',n:'Flag: Ukraine',c:'Flags'},{e:'🇮🇱',n:'Flag: Israel',c:'Flags'},
      {e:'🇨🇴',n:'Flag: Colombia',c:'Flags'},{e:'🇨🇱',n:'Flag: Chile',c:'Flags'},
      {e:'🇵🇪',n:'Flag: Peru',c:'Flags'},{e:'🇪🇺',n:'Flag: European Union',c:'Flags'},
      {e:'🇺🇳',n:'Flag: United Nations',c:'Flags'}
    ]
  };

  function epjGetToned(emoji) {
    if (!EPJ.tone) return emoji;
    var base = emoji.replace(/[\uD83C][\uDFFB-\uDFFF]/g,'');
    var cp = base.codePointAt(0);
    if ((cp >= 0x1F466 && cp <= 0x1F9D1) || (cp >= 0x1F91A && cp <= 0x1F91F) ||
        (cp >= 0x1F918 && cp <= 0x1F91E) || cp===0x1F44B || cp===0x1F91A ||
        (cp >= 0x1F446 && cp <= 0x1F44F) || cp===0x270B || cp===0x270C || cp===0x270D ||
        cp===0x1F485 || cp===0x1F4AA || cp===0x1F595 || cp===0x261D ||
        (cp >= 0x1F590 && cp <= 0x1F596)) {
      return base + EPJ.tone;
    }
    return emoji;
  }

  function epjGetCodePoints(emoji) {
    var points = [];
    for (var i = 0; i < emoji.length; ) {
      var cp = emoji.codePointAt(i);
      points.push('U+' + cp.toString(16).toUpperCase().padStart(4,'0'));
      i += cp > 0xFFFF ? 2 : 1;
    }
    return points.join(' ');
  }

  function epjGetEntity(emoji) {
    var entities = [];
    for (var i = 0; i < emoji.length; ) {
      var cp = emoji.codePointAt(i);
      if (cp !== 0xFE0F && cp !== 0x200D) {
        entities.push('&#x' + cp.toString(16).toUpperCase() + ';');
      }
      i += cp > 0xFFFF ? 2 : 1;
    }
    return entities.join('');
  }

  function epjFiltered() {
    var q = EPJ.query.toLowerCase().trim();
    return EPJ.data.filter(function(item) {
      if (EPJ.cat !== 'all' && item.c !== EPJ.cat) return false;
      if (q && item.n.toLowerCase().indexOf(q) === -1 && item.e.indexOf(q) === -1) return false;
      return true;
    });
  }

  function epjRender() {
    var grid = document.getElementById('ep-emoji-grid');
    var title = document.getElementById('ep-grid-title');
    var items = epjFiltered();
    var catLabel = EPJ.catLabel[EPJ.cat] || EPJ.cat;
    title.textContent = catLabel + ' (' + items.length + '件)';
    if (items.length === 0) {
      grid.innerHTML = '<div class="ep-empty">"' + EPJ.query + '" に一致する絵文字がありません</div>';
      return;
    }
    grid.innerHTML = items.map(function(item) {
      var display = epjGetToned(item.e);
      return '<button class="ep-emoji-btn" title="' + item.n + '" onclick="epjaClick(\'' +
        item.e.replace(/'/g,"\\'") + '\',\'' + item.n.replace(/'/g,"\\'") + '\',\'' + item.c + '\')">' +
        display + '</button>';
    }).join('');
  }

  function epjRenderRecent() {
    var grid = document.getElementById('ep-recent-grid');
    var recent = epjGetRecent();
    if (recent.length === 0) {
      grid.innerHTML = '<span class="ep-no-recent">まだ使った絵文字はありません</span>';
      return;
    }
    grid.innerHTML = recent.map(function(item) {
      return '<button class="ep-emoji-btn" title="' + item.n + '" onclick="epjaClick(\'' +
        item.e.replace(/'/g,"\\'") + '\',\'' + item.n.replace(/'/g,"\\'") + '\',\'' + item.c + '\')">' +
        epjGetToned(item.e) + '</button>';
    }).join('');
  }

  function epjGetRecent() {
    try {
      return JSON.parse(localStorage.getItem('epja_recent') || '[]');
    } catch(e) { return []; }
  }

  function epjAddRecent(emoji, name, cat) {
    var recent = epjGetRecent().filter(function(r) { return r.e !== emoji; });
    recent.unshift({e:emoji,n:name,c:cat});
    recent = recent.slice(0,24);
    try { localStorage.setItem('epja_recent', JSON.stringify(recent)); } catch(e){}
    epjRenderRecent();
  }

  function epjShowInfo(emoji, name, cat) {
    EPJ.selected = {e:emoji,n:name,c:cat};
    var panel = document.getElementById('ep-info-panel');
    panel.classList.add('visible');
    document.getElementById('ep-info-emoji').textContent = epjGetToned(emoji);
    document.getElementById('ep-info-name').textContent = name;
    document.getElementById('ep-info-unicode').textContent = epjGetCodePoints(emoji);
    document.getElementById('ep-info-entity').textContent = epjGetEntity(emoji);
    document.getElementById('ep-info-category').textContent = EPJ.catLabel[cat] || cat;
  }

  window.epjaClick = function(emoji, name, cat) {
    epjCopy(epjGetToned(emoji));
    epjAddRecent(emoji, name, cat);
    epjShowInfo(emoji, name, cat);
  };

  window.epjaCopySelected = function() {
    if (EPJ.selected) {
      epjCopy(epjGetToned(EPJ.selected.e));
    }
  };

  function epjCopy(text) {
    if (navigator.clipboard && navigator.clipboard.writeText) {
      navigator.clipboard.writeText(text).then(function() { epjToast('コピーしました: ' + text); });
    } else {
      var ta = document.createElement('textarea');
      ta.value = text; ta.style.position='fixed'; ta.style.opacity='0';
      document.body.appendChild(ta); ta.select();
      document.execCommand('copy');
      document.body.removeChild(ta);
      epjToast('コピーしました: ' + text);
    }
  }

  function epjToast(msg) {
    var t = document.getElementById('ep-toast');
    t.textContent = msg;
    t.classList.add('show');
    setTimeout(function() { t.classList.remove('show'); }, 2200);
  }

  window.epjaSearch = function() {
    EPJ.query = document.getElementById('ep-search').value;
    epjRender();
  };

  window.epjaSetTab = function(btn) {
    document.querySelectorAll('.ep-tab').forEach(function(b) { b.classList.remove('active'); });
    btn.classList.add('active');
    EPJ.cat = btn.getAttribute('data-cat');
    epjRender();
  };

  window.epjaSetTone = function(btn, tone) {
    document.querySelectorAll('.ep-tone-btn').forEach(function(b) { b.classList.remove('active'); });
    btn.classList.add('active');
    EPJ.tone = tone;
    epjRender();
    epjRenderRecent();
    if (EPJ.selected) {
      document.getElementById('ep-info-emoji').textContent = epjGetToned(EPJ.selected.e);
    }
  };

  epjRender();
  epjRenderRecent();
})();
</script>

</div>

---

**ビジネスの効率化にはfreee**
<a href="https://px.a8.net/svt/ejp?a8mat=4B3QAZ+7YYYCY+3SPO+9FHKUP" rel="nofollow">freeeを無料で試す</a>
