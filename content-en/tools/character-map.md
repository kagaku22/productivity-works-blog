---
title: "Unicode Character Map"
date: 2025-05-16
description: "Browse and copy Unicode characters by category. Find arrows, math symbols, currency signs, Greek letters, box-drawing characters, and more. Instantly copy any character with its code point, HTML entity, CSS content, and UTF-8 hex."
categories: ["Free Tools"]
slug: "character-map"
ShowToc: false
cover:
  image: "/images/covers/character-map.png"
  alt: "Unicode Character Map"
aliases:
  - "/tools/unicode-table/"
  - "/tools/special-characters/"
---

Browse Unicode characters by category or search by name. Click any character to copy it — along with its code point, HTML entity, CSS `content` value, and UTF-8 hex bytes.

<div id="cm-app">

<style>
#cm-app {
  font-family: system-ui, -apple-system, sans-serif;
  max-width: 980px;
  margin: 0 auto;
  color: #1a1a1a;
}
#cm-app *, #cm-app *::before, #cm-app *::after { box-sizing: border-box; margin: 0; padding: 0; }

/* ── Controls ── */
#cm-app .cm-controls {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 18px;
  align-items: center;
}
#cm-app .cm-search {
  flex: 1 1 220px;
  padding: 9px 14px;
  border: 1.5px solid #d1d5db;
  border-radius: 8px;
  font-size: 14px;
  outline: none;
  transition: border-color .2s;
}
#cm-app .cm-search:focus { border-color: #6366f1; }
#cm-app .cm-cat-select {
  flex: 1 1 180px;
  padding: 9px 12px;
  border: 1.5px solid #d1d5db;
  border-radius: 8px;
  font-size: 14px;
  background: #fff;
  cursor: pointer;
  outline: none;
}
#cm-app .cm-cat-select:focus { border-color: #6366f1; }

/* ── Category tabs ── */
#cm-app .cm-tabs {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-bottom: 16px;
}
#cm-app .cm-tab {
  padding: 6px 13px;
  border: 1.5px solid #e5e7eb;
  border-radius: 20px;
  font-size: 13px;
  background: #f9fafb;
  cursor: pointer;
  transition: background .15s, border-color .15s, color .15s;
  user-select: none;
}
#cm-app .cm-tab:hover { background: #ede9fe; border-color: #a5b4fc; }
#cm-app .cm-tab.active { background: #6366f1; border-color: #6366f1; color: #fff; font-weight: 600; }

/* ── Grid ── */
#cm-app .cm-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(52px, 1fr));
  gap: 6px;
  margin-bottom: 20px;
  min-height: 80px;
}
#cm-app .cm-cell {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 52px;
  border: 1.5px solid #e5e7eb;
  border-radius: 8px;
  font-size: 22px;
  cursor: pointer;
  background: #fff;
  transition: background .15s, border-color .15s, transform .1s;
  user-select: none;
}
#cm-app .cm-cell:hover {
  background: #ede9fe;
  border-color: #6366f1;
  transform: scale(1.12);
  z-index: 2;
}
#cm-app .cm-cell:active { transform: scale(1.04); }
#cm-app .cm-cell .cm-tip {
  display: none;
  position: absolute;
  bottom: calc(100% + 6px);
  left: 50%;
  transform: translateX(-50%);
  background: #1e1b4b;
  color: #fff;
  font-size: 11px;
  padding: 5px 8px;
  border-radius: 6px;
  white-space: nowrap;
  pointer-events: none;
  z-index: 10;
  line-height: 1.5;
  text-align: center;
}
#cm-app .cm-cell:hover .cm-tip { display: block; }

/* ── Detail panel ── */
#cm-app .cm-detail {
  background: #f8fafc;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  padding: 16px 20px;
  margin-bottom: 20px;
  display: none;
}
#cm-app .cm-detail.visible { display: block; }
#cm-app .cm-detail-char {
  font-size: 48px;
  line-height: 1;
  margin-bottom: 10px;
}
#cm-app .cm-detail-name {
  font-size: 15px;
  font-weight: 700;
  color: #4f46e5;
  margin-bottom: 10px;
}
#cm-app .cm-detail-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(210px, 1fr));
  gap: 8px;
}
#cm-app .cm-detail-row {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 7px;
  padding: 8px 12px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 8px;
}
#cm-app .cm-detail-label {
  font-size: 11px;
  color: #64748b;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: .04em;
  white-space: nowrap;
}
#cm-app .cm-detail-val {
  font-size: 13px;
  font-family: monospace;
  color: #1e293b;
  word-break: break-all;
}
#cm-app .cm-copy-btn {
  padding: 3px 10px;
  background: #6366f1;
  color: #fff;
  border: none;
  border-radius: 5px;
  font-size: 12px;
  cursor: pointer;
  white-space: nowrap;
  transition: background .15s;
}
#cm-app .cm-copy-btn:hover { background: #4f46e5; }

/* ── Recently copied ── */
#cm-app .cm-recent-section { margin-bottom: 22px; }
#cm-app .cm-section-title {
  font-size: 13px;
  font-weight: 700;
  color: #6b7280;
  text-transform: uppercase;
  letter-spacing: .06em;
  margin-bottom: 8px;
}
#cm-app .cm-recent-row {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}
#cm-app .cm-recent-chip {
  display: flex;
  align-items: center;
  gap: 5px;
  padding: 5px 10px;
  background: #f1f5f9;
  border: 1px solid #e2e8f0;
  border-radius: 20px;
  font-size: 18px;
  cursor: pointer;
  transition: background .15s;
  user-select: none;
}
#cm-app .cm-recent-chip:hover { background: #ede9fe; border-color: #a5b4fc; }
#cm-app .cm-recent-chip .chip-label { font-size: 11px; color: #64748b; }

/* ── Toast ── */
#cm-app .cm-toast {
  position: fixed;
  bottom: 24px;
  right: 24px;
  background: #1e1b4b;
  color: #fff;
  padding: 10px 18px;
  border-radius: 8px;
  font-size: 14px;
  z-index: 9999;
  opacity: 0;
  transform: translateY(10px);
  transition: opacity .25s, transform .25s;
  pointer-events: none;
}
#cm-app .cm-toast.show { opacity: 1; transform: translateY(0); }

/* ── No results ── */
#cm-app .cm-empty {
  grid-column: 1/-1;
  text-align: center;
  color: #9ca3af;
  font-size: 14px;
  padding: 30px 0;
}

/* ── Responsive ── */
@media (max-width: 480px) {
  #cm-app .cm-grid { grid-template-columns: repeat(auto-fill, minmax(44px, 1fr)); gap: 4px; }
  #cm-app .cm-cell { height: 44px; font-size: 18px; }
  #cm-app .cm-detail-char { font-size: 36px; }
}
</style>

<!-- Controls -->
<div class="cm-controls">
  <input class="cm-search" id="cm-search" type="search" placeholder="Search by name (e.g. arrow, heart, star)..." autocomplete="off" />
</div>

<!-- Category tabs -->
<div class="cm-tabs" id="cm-tabs"></div>

<!-- Recently copied -->
<div class="cm-recent-section" id="cm-recent-section" style="display:none;">
  <div class="cm-section-title">Recently Copied</div>
  <div class="cm-recent-row" id="cm-recent-row"></div>
</div>

<!-- Detail panel -->
<div class="cm-detail" id="cm-detail">
  <div class="cm-detail-char" id="cm-detail-char"></div>
  <div class="cm-detail-name" id="cm-detail-name"></div>
  <div class="cm-detail-grid" id="cm-detail-grid"></div>
</div>

<!-- Character grid -->
<div class="cm-grid" id="cm-grid"></div>

<!-- Toast -->
<div class="cm-toast" id="cm-toast"></div>

<script>
(function(){
'use strict';

/* ── Character database ── */
const CATS = [
  { id:'latin',    label:'Basic Latin' },
  { id:'latin-ext',label:'Latin Extended' },
  { id:'greek',    label:'Greek' },
  { id:'cyrillic', label:'Cyrillic' },
  { id:'arrows',   label:'Arrows' },
  { id:'math',     label:'Math Symbols' },
  { id:'box',      label:'Box Drawing' },
  { id:'currency', label:'Currency' },
  { id:'dingbats', label:'Dingbats' },
];

function makeRange(start, end, names) {
  const out = [];
  for (let cp = start; cp <= end; cp++) {
    out.push({ cp, name: names[cp] || '' });
  }
  return out;
}

/* Named character data (curated subset; full names for common chars) */
const NAMED = {};
const define = (cp, name) => { NAMED[cp] = name; };

// Basic Latin printable (0x20–0x7E)
const latinNames = {
  0x20:'SPACE',0x21:'EXCLAMATION MARK',0x22:'QUOTATION MARK',0x23:'NUMBER SIGN',
  0x24:'DOLLAR SIGN',0x25:'PERCENT SIGN',0x26:'AMPERSAND',0x27:'APOSTROPHE',
  0x28:'LEFT PARENTHESIS',0x29:'RIGHT PARENTHESIS',0x2A:'ASTERISK',0x2B:'PLUS SIGN',
  0x2C:'COMMA',0x2D:'HYPHEN-MINUS',0x2E:'FULL STOP',0x2F:'SOLIDUS',
  0x30:'DIGIT ZERO',0x31:'DIGIT ONE',0x32:'DIGIT TWO',0x33:'DIGIT THREE',
  0x34:'DIGIT FOUR',0x35:'DIGIT FIVE',0x36:'DIGIT SIX',0x37:'DIGIT SEVEN',
  0x38:'DIGIT EIGHT',0x39:'DIGIT NINE',0x3A:'COLON',0x3B:'SEMICOLON',
  0x3C:'LESS-THAN SIGN',0x3D:'EQUALS SIGN',0x3E:'GREATER-THAN SIGN',0x3F:'QUESTION MARK',
  0x40:'COMMERCIAL AT',0x41:'LATIN CAPITAL LETTER A',0x42:'LATIN CAPITAL LETTER B',
  0x43:'LATIN CAPITAL LETTER C',0x44:'LATIN CAPITAL LETTER D',0x45:'LATIN CAPITAL LETTER E',
  0x46:'LATIN CAPITAL LETTER F',0x47:'LATIN CAPITAL LETTER G',0x48:'LATIN CAPITAL LETTER H',
  0x49:'LATIN CAPITAL LETTER I',0x4A:'LATIN CAPITAL LETTER J',0x4B:'LATIN CAPITAL LETTER K',
  0x4C:'LATIN CAPITAL LETTER L',0x4D:'LATIN CAPITAL LETTER M',0x4E:'LATIN CAPITAL LETTER N',
  0x4F:'LATIN CAPITAL LETTER O',0x50:'LATIN CAPITAL LETTER P',0x51:'LATIN CAPITAL LETTER Q',
  0x52:'LATIN CAPITAL LETTER R',0x53:'LATIN CAPITAL LETTER S',0x54:'LATIN CAPITAL LETTER T',
  0x55:'LATIN CAPITAL LETTER U',0x56:'LATIN CAPITAL LETTER V',0x57:'LATIN CAPITAL LETTER W',
  0x58:'LATIN CAPITAL LETTER X',0x59:'LATIN CAPITAL LETTER Y',0x5A:'LATIN CAPITAL LETTER Z',
  0x5B:'LEFT SQUARE BRACKET',0x5C:'REVERSE SOLIDUS',0x5D:'RIGHT SQUARE BRACKET',
  0x5E:'CIRCUMFLEX ACCENT',0x5F:'LOW LINE',0x60:'GRAVE ACCENT',
  0x61:'LATIN SMALL LETTER A',0x62:'LATIN SMALL LETTER B',0x63:'LATIN SMALL LETTER C',
  0x64:'LATIN SMALL LETTER D',0x65:'LATIN SMALL LETTER E',0x66:'LATIN SMALL LETTER F',
  0x67:'LATIN SMALL LETTER G',0x68:'LATIN SMALL LETTER H',0x69:'LATIN SMALL LETTER I',
  0x6A:'LATIN SMALL LETTER J',0x6B:'LATIN SMALL LETTER K',0x6C:'LATIN SMALL LETTER L',
  0x6D:'LATIN SMALL LETTER M',0x6E:'LATIN SMALL LETTER N',0x6F:'LATIN SMALL LETTER O',
  0x70:'LATIN SMALL LETTER P',0x71:'LATIN SMALL LETTER Q',0x72:'LATIN SMALL LETTER R',
  0x73:'LATIN SMALL LETTER S',0x74:'LATIN SMALL LETTER T',0x75:'LATIN SMALL LETTER U',
  0x76:'LATIN SMALL LETTER V',0x77:'LATIN SMALL LETTER W',0x78:'LATIN SMALL LETTER X',
  0x79:'LATIN SMALL LETTER Y',0x7A:'LATIN SMALL LETTER Z',0x7B:'LEFT CURLY BRACKET',
  0x7C:'VERTICAL LINE',0x7D:'RIGHT CURLY BRACKET',0x7E:'TILDE',
};

// Latin Extended (selected)
const latinExtNames = {
  0xC0:'LATIN CAPITAL LETTER A WITH GRAVE',0xC1:'LATIN CAPITAL LETTER A WITH ACUTE',
  0xC2:'LATIN CAPITAL LETTER A WITH CIRCUMFLEX',0xC3:'LATIN CAPITAL LETTER A WITH TILDE',
  0xC4:'LATIN CAPITAL LETTER A WITH DIAERESIS',0xC5:'LATIN CAPITAL LETTER A WITH RING ABOVE',
  0xC6:'LATIN CAPITAL LETTER AE',0xC7:'LATIN CAPITAL LETTER C WITH CEDILLA',
  0xC8:'LATIN CAPITAL LETTER E WITH GRAVE',0xC9:'LATIN CAPITAL LETTER E WITH ACUTE',
  0xCA:'LATIN CAPITAL LETTER E WITH CIRCUMFLEX',0xCB:'LATIN CAPITAL LETTER E WITH DIAERESIS',
  0xCC:'LATIN CAPITAL LETTER I WITH GRAVE',0xCD:'LATIN CAPITAL LETTER I WITH ACUTE',
  0xCE:'LATIN CAPITAL LETTER I WITH CIRCUMFLEX',0xCF:'LATIN CAPITAL LETTER I WITH DIAERESIS',
  0xD0:'LATIN CAPITAL LETTER ETH',0xD1:'LATIN CAPITAL LETTER N WITH TILDE',
  0xD2:'LATIN CAPITAL LETTER O WITH GRAVE',0xD3:'LATIN CAPITAL LETTER O WITH ACUTE',
  0xD4:'LATIN CAPITAL LETTER O WITH CIRCUMFLEX',0xD5:'LATIN CAPITAL LETTER O WITH TILDE',
  0xD6:'LATIN CAPITAL LETTER O WITH DIAERESIS',0xD7:'MULTIPLICATION SIGN',
  0xD8:'LATIN CAPITAL LETTER O WITH STROKE',0xD9:'LATIN CAPITAL LETTER U WITH GRAVE',
  0xDA:'LATIN CAPITAL LETTER U WITH ACUTE',0xDB:'LATIN CAPITAL LETTER U WITH CIRCUMFLEX',
  0xDC:'LATIN CAPITAL LETTER U WITH DIAERESIS',0xDD:'LATIN CAPITAL LETTER Y WITH ACUTE',
  0xDE:'LATIN CAPITAL LETTER THORN',0xDF:'LATIN SMALL LETTER SHARP S',
  0xE0:'LATIN SMALL LETTER A WITH GRAVE',0xE1:'LATIN SMALL LETTER A WITH ACUTE',
  0xE2:'LATIN SMALL LETTER A WITH CIRCUMFLEX',0xE3:'LATIN SMALL LETTER A WITH TILDE',
  0xE4:'LATIN SMALL LETTER A WITH DIAERESIS',0xE5:'LATIN SMALL LETTER A WITH RING ABOVE',
  0xE6:'LATIN SMALL LETTER AE',0xE7:'LATIN SMALL LETTER C WITH CEDILLA',
  0xE8:'LATIN SMALL LETTER E WITH GRAVE',0xE9:'LATIN SMALL LETTER E WITH ACUTE',
  0xEA:'LATIN SMALL LETTER E WITH CIRCUMFLEX',0xEB:'LATIN SMALL LETTER E WITH DIAERESIS',
  0xEC:'LATIN SMALL LETTER I WITH GRAVE',0xED:'LATIN SMALL LETTER I WITH ACUTE',
  0xEE:'LATIN SMALL LETTER I WITH CIRCUMFLEX',0xEF:'LATIN SMALL LETTER I WITH DIAERESIS',
  0xF0:'LATIN SMALL LETTER ETH',0xF1:'LATIN SMALL LETTER N WITH TILDE',
  0xF2:'LATIN SMALL LETTER O WITH GRAVE',0xF3:'LATIN SMALL LETTER O WITH ACUTE',
  0xF4:'LATIN SMALL LETTER O WITH CIRCUMFLEX',0xF5:'LATIN SMALL LETTER O WITH TILDE',
  0xF6:'LATIN SMALL LETTER O WITH DIAERESIS',0xF7:'DIVISION SIGN',
  0xF8:'LATIN SMALL LETTER O WITH STROKE',0xF9:'LATIN SMALL LETTER U WITH GRAVE',
  0xFA:'LATIN SMALL LETTER U WITH ACUTE',0xFB:'LATIN SMALL LETTER U WITH CIRCUMFLEX',
  0xFC:'LATIN SMALL LETTER U WITH DIAERESIS',0xFD:'LATIN SMALL LETTER Y WITH ACUTE',
  0xFE:'LATIN SMALL LETTER THORN',0xFF:'LATIN SMALL LETTER Y WITH DIAERESIS',
  // Latin Extended-A
  0x100:'LATIN CAPITAL LETTER A WITH MACRON',0x101:'LATIN SMALL LETTER A WITH MACRON',
  0x102:'LATIN CAPITAL LETTER A WITH BREVE',0x103:'LATIN SMALL LETTER A WITH BREVE',
  0x110:'LATIN CAPITAL LETTER D WITH STROKE',0x111:'LATIN SMALL LETTER D WITH STROKE',
  0x126:'LATIN CAPITAL LETTER H WITH STROKE',0x127:'LATIN SMALL LETTER H WITH STROKE',
  0x131:'LATIN SMALL LETTER DOTLESS I',0x141:'LATIN CAPITAL LETTER L WITH STROKE',
  0x142:'LATIN SMALL LETTER L WITH STROKE',0x152:'LATIN CAPITAL LIGATURE OE',
  0x153:'LATIN SMALL LIGATURE OE',0x160:'LATIN CAPITAL LETTER S WITH CARON',
  0x161:'LATIN SMALL LETTER S WITH CARON',0x178:'LATIN CAPITAL LETTER Y WITH DIAERESIS',
  0x17D:'LATIN CAPITAL LETTER Z WITH CARON',0x17E:'LATIN SMALL LETTER Z WITH CARON',
};

// Greek (0x370–0x3FF core)
const greekNames = {
  0x391:'GREEK CAPITAL LETTER ALPHA',0x392:'GREEK CAPITAL LETTER BETA',
  0x393:'GREEK CAPITAL LETTER GAMMA',0x394:'GREEK CAPITAL LETTER DELTA',
  0x395:'GREEK CAPITAL LETTER EPSILON',0x396:'GREEK CAPITAL LETTER ZETA',
  0x397:'GREEK CAPITAL LETTER ETA',0x398:'GREEK CAPITAL LETTER THETA',
  0x399:'GREEK CAPITAL LETTER IOTA',0x39A:'GREEK CAPITAL LETTER KAPPA',
  0x39B:'GREEK CAPITAL LETTER LAMDA',0x39C:'GREEK CAPITAL LETTER MU',
  0x39D:'GREEK CAPITAL LETTER NU',0x39E:'GREEK CAPITAL LETTER XI',
  0x39F:'GREEK CAPITAL LETTER OMICRON',0x3A0:'GREEK CAPITAL LETTER PI',
  0x3A1:'GREEK CAPITAL LETTER RHO',0x3A3:'GREEK CAPITAL LETTER SIGMA',
  0x3A4:'GREEK CAPITAL LETTER TAU',0x3A5:'GREEK CAPITAL LETTER UPSILON',
  0x3A6:'GREEK CAPITAL LETTER PHI',0x3A7:'GREEK CAPITAL LETTER CHI',
  0x3A8:'GREEK CAPITAL LETTER PSI',0x3A9:'GREEK CAPITAL LETTER OMEGA',
  0x3B1:'GREEK SMALL LETTER ALPHA',0x3B2:'GREEK SMALL LETTER BETA',
  0x3B3:'GREEK SMALL LETTER GAMMA',0x3B4:'GREEK SMALL LETTER DELTA',
  0x3B5:'GREEK SMALL LETTER EPSILON',0x3B6:'GREEK SMALL LETTER ZETA',
  0x3B7:'GREEK SMALL LETTER ETA',0x3B8:'GREEK SMALL LETTER THETA',
  0x3B9:'GREEK SMALL LETTER IOTA',0x3BA:'GREEK SMALL LETTER KAPPA',
  0x3BB:'GREEK SMALL LETTER LAMDA',0x3BC:'GREEK SMALL LETTER MU',
  0x3BD:'GREEK SMALL LETTER NU',0x3BE:'GREEK SMALL LETTER XI',
  0x3BF:'GREEK SMALL LETTER OMICRON',0x3C0:'GREEK SMALL LETTER PI',
  0x3C1:'GREEK SMALL LETTER RHO',0x3C2:'GREEK SMALL LETTER FINAL SIGMA',
  0x3C3:'GREEK SMALL LETTER SIGMA',0x3C4:'GREEK SMALL LETTER TAU',
  0x3C5:'GREEK SMALL LETTER UPSILON',0x3C6:'GREEK SMALL LETTER PHI',
  0x3C7:'GREEK SMALL LETTER CHI',0x3C8:'GREEK SMALL LETTER PSI',
  0x3C9:'GREEK SMALL LETTER OMEGA',
};

// Cyrillic (0x410–0x44F)
const cyrillicNames = {
  0x410:'CYRILLIC CAPITAL LETTER A',0x411:'CYRILLIC CAPITAL LETTER BE',
  0x412:'CYRILLIC CAPITAL LETTER VE',0x413:'CYRILLIC CAPITAL LETTER GHE',
  0x414:'CYRILLIC CAPITAL LETTER DE',0x415:'CYRILLIC CAPITAL LETTER IE',
  0x416:'CYRILLIC CAPITAL LETTER ZHE',0x417:'CYRILLIC CAPITAL LETTER ZE',
  0x418:'CYRILLIC CAPITAL LETTER I',0x419:'CYRILLIC CAPITAL LETTER SHORT I',
  0x41A:'CYRILLIC CAPITAL LETTER KA',0x41B:'CYRILLIC CAPITAL LETTER EL',
  0x41C:'CYRILLIC CAPITAL LETTER EM',0x41D:'CYRILLIC CAPITAL LETTER EN',
  0x41E:'CYRILLIC CAPITAL LETTER O',0x41F:'CYRILLIC CAPITAL LETTER PE',
  0x420:'CYRILLIC CAPITAL LETTER ER',0x421:'CYRILLIC CAPITAL LETTER ES',
  0x422:'CYRILLIC CAPITAL LETTER TE',0x423:'CYRILLIC CAPITAL LETTER U',
  0x424:'CYRILLIC CAPITAL LETTER EF',0x425:'CYRILLIC CAPITAL LETTER HA',
  0x426:'CYRILLIC CAPITAL LETTER TSE',0x427:'CYRILLIC CAPITAL LETTER CHE',
  0x428:'CYRILLIC CAPITAL LETTER SHA',0x429:'CYRILLIC CAPITAL LETTER SHCHA',
  0x42A:'CYRILLIC CAPITAL LETTER HARD SIGN',0x42B:'CYRILLIC CAPITAL LETTER YERU',
  0x42C:'CYRILLIC CAPITAL LETTER SOFT SIGN',0x42D:'CYRILLIC CAPITAL LETTER E',
  0x42E:'CYRILLIC CAPITAL LETTER YU',0x42F:'CYRILLIC CAPITAL LETTER YA',
  0x430:'CYRILLIC SMALL LETTER A',0x431:'CYRILLIC SMALL LETTER BE',
  0x432:'CYRILLIC SMALL LETTER VE',0x433:'CYRILLIC SMALL LETTER GHE',
  0x434:'CYRILLIC SMALL LETTER DE',0x435:'CYRILLIC SMALL LETTER IE',
  0x436:'CYRILLIC SMALL LETTER ZHE',0x437:'CYRILLIC SMALL LETTER ZE',
  0x438:'CYRILLIC SMALL LETTER I',0x439:'CYRILLIC SMALL LETTER SHORT I',
  0x43A:'CYRILLIC SMALL LETTER KA',0x43B:'CYRILLIC SMALL LETTER EL',
  0x43C:'CYRILLIC SMALL LETTER EM',0x43D:'CYRILLIC SMALL LETTER EN',
  0x43E:'CYRILLIC SMALL LETTER O',0x43F:'CYRILLIC SMALL LETTER PE',
  0x440:'CYRILLIC SMALL LETTER ER',0x441:'CYRILLIC SMALL LETTER ES',
  0x442:'CYRILLIC SMALL LETTER TE',0x443:'CYRILLIC SMALL LETTER U',
  0x444:'CYRILLIC SMALL LETTER EF',0x445:'CYRILLIC SMALL LETTER HA',
  0x446:'CYRILLIC SMALL LETTER TSE',0x447:'CYRILLIC SMALL LETTER CHE',
  0x448:'CYRILLIC SMALL LETTER SHA',0x449:'CYRILLIC SMALL LETTER SHCHA',
  0x44A:'CYRILLIC SMALL LETTER HARD SIGN',0x44B:'CYRILLIC SMALL LETTER YERU',
  0x44C:'CYRILLIC SMALL LETTER SOFT SIGN',0x44D:'CYRILLIC SMALL LETTER E',
  0x44E:'CYRILLIC SMALL LETTER YU',0x44F:'CYRILLIC SMALL LETTER YA',
};

// Arrows (selected)
const arrowNames = {
  0x2190:'LEFTWARDS ARROW',0x2191:'UPWARDS ARROW',0x2192:'RIGHTWARDS ARROW',
  0x2193:'DOWNWARDS ARROW',0x2194:'LEFT RIGHT ARROW',0x2195:'UP DOWN ARROW',
  0x2196:'NORTH WEST ARROW',0x2197:'NORTH EAST ARROW',0x2198:'SOUTH EAST ARROW',
  0x2199:'SOUTH WEST ARROW',0x219A:'LEFTWARDS ARROW WITH STROKE',
  0x219B:'RIGHTWARDS ARROW WITH STROKE',0x219C:'LEFTWARDS WAVE ARROW',
  0x219D:'RIGHTWARDS WAVE ARROW',0x219E:'LEFTWARDS TWO HEADED ARROW',
  0x219F:'UPWARDS TWO HEADED ARROW',0x21A0:'RIGHTWARDS TWO HEADED ARROW',
  0x21A1:'DOWNWARDS TWO HEADED ARROW',0x21A2:'LEFTWARDS ARROW WITH TAIL',
  0x21A3:'RIGHTWARDS ARROW WITH TAIL',0x21A4:'LEFTWARDS ARROW FROM BAR',
  0x21A6:'RIGHTWARDS ARROW FROM BAR',0x21A9:'LEFTWARDS ARROW WITH HOOK',
  0x21AA:'RIGHTWARDS ARROW WITH HOOK',0x21AB:'LEFTWARDS ARROW WITH LOOP',
  0x21AC:'RIGHTWARDS ARROW WITH LOOP',0x21AD:'LEFT RIGHT WAVE ARROW',
  0x21AE:'LEFT RIGHT ARROW WITH STROKE',0x21B0:'UPWARDS ARROW WITH TIP LEFTWARDS',
  0x21B1:'UPWARDS ARROW WITH TIP RIGHTWARDS',0x21B2:'DOWNWARDS ARROW WITH TIP LEFTWARDS',
  0x21B3:'DOWNWARDS ARROW WITH TIP RIGHTWARDS',0x21B4:'RIGHTWARDS ARROW WITH CORNER DOWNWARDS',
  0x21B5:'DOWNWARDS ARROW WITH CORNER LEFTWARDS',0x21B6:'ANTICLOCKWISE TOP SEMICIRCLE ARROW',
  0x21B7:'CLOCKWISE TOP SEMICIRCLE ARROW',0x21BA:'ANTICLOCKWISE OPEN CIRCLE ARROW',
  0x21BB:'CLOCKWISE OPEN CIRCLE ARROW',0x21BC:'LEFTWARDS HARPOON WITH BARB UPWARDS',
  0x21BD:'LEFTWARDS HARPOON WITH BARB DOWNWARDS',0x21BE:'UPWARDS HARPOON WITH BARB RIGHTWARDS',
  0x21BF:'UPWARDS HARPOON WITH BARB LEFTWARDS',0x21C0:'RIGHTWARDS HARPOON WITH BARB UPWARDS',
  0x21C4:'RIGHTWARDS ARROW OVER LEFTWARDS ARROW',0x21C6:'LEFTWARDS ARROW OVER RIGHTWARDS ARROW',
  0x21C7:'LEFTWARDS PAIRED ARROWS',0x21C8:'UPWARDS PAIRED ARROWS',
  0x21C9:'RIGHTWARDS PAIRED ARROWS',0x21CA:'DOWNWARDS PAIRED ARROWS',
  0x21CC:'RIGHTWARDS HARPOON OVER LEFTWARDS HARPOON',
  0x21D0:'LEFTWARDS DOUBLE ARROW',0x21D1:'UPWARDS DOUBLE ARROW',
  0x21D2:'RIGHTWARDS DOUBLE ARROW',0x21D3:'DOWNWARDS DOUBLE ARROW',
  0x21D4:'LEFT RIGHT DOUBLE ARROW',0x21D5:'UP DOWN DOUBLE ARROW',
  0x21E6:'LEFTWARDS WHITE ARROW',0x21E7:'UPWARDS WHITE ARROW',
  0x21E8:'RIGHTWARDS WHITE ARROW',0x21E9:'DOWNWARDS WHITE ARROW',
  0x27A1:'BLACK RIGHTWARDS ARROW',0x2B05:'LEFTWARDS BLACK ARROW',
  0x2B06:'UPWARDS BLACK ARROW',0x2B07:'DOWNWARDS BLACK ARROW',
  0x2B0C:'LEFT RIGHT BLACK ARROW',0x2B0D:'UP DOWN BLACK ARROW',
};

// Math symbols (selected)
const mathNames = {
  0x2200:'FOR ALL',0x2201:'COMPLEMENT',0x2202:'PARTIAL DIFFERENTIAL',
  0x2203:'THERE EXISTS',0x2204:'THERE DOES NOT EXIST',0x2205:'EMPTY SET',
  0x2206:'INCREMENT',0x2207:'NABLA',0x2208:'ELEMENT OF',0x2209:'NOT AN ELEMENT OF',
  0x220A:'SMALL ELEMENT OF',0x220B:'CONTAINS AS MEMBER',0x220C:'DOES NOT CONTAIN AS MEMBER',
  0x220F:'N-ARY PRODUCT',0x2210:'N-ARY COPRODUCT',0x2211:'N-ARY SUMMATION',
  0x2212:'MINUS SIGN',0x2213:'MINUS-OR-PLUS SIGN',0x2214:'DOT PLUS',
  0x2215:'DIVISION SLASH',0x2216:'SET MINUS',0x2217:'ASTERISK OPERATOR',
  0x2218:'RING OPERATOR',0x2219:'BULLET OPERATOR',0x221A:'SQUARE ROOT',
  0x221B:'CUBE ROOT',0x221C:'FOURTH ROOT',0x221D:'PROPORTIONAL TO',
  0x221E:'INFINITY',0x221F:'RIGHT ANGLE',0x2220:'ANGLE',
  0x2221:'MEASURED ANGLE',0x2222:'SPHERICAL ANGLE',0x2223:'DIVIDES',
  0x2224:'DOES NOT DIVIDE',0x2225:'PARALLEL TO',0x2226:'NOT PARALLEL TO',
  0x2227:'LOGICAL AND',0x2228:'LOGICAL OR',0x2229:'INTERSECTION',
  0x222A:'UNION',0x222B:'INTEGRAL',0x222C:'DOUBLE INTEGRAL',
  0x222D:'TRIPLE INTEGRAL',0x222E:'CONTOUR INTEGRAL',0x2234:'THEREFORE',
  0x2235:'BECAUSE',0x2236:'RATIO',0x2237:'PROPORTION',
  0x223C:'TILDE OPERATOR',0x2248:'ALMOST EQUAL TO',0x2260:'NOT EQUAL TO',
  0x2261:'IDENTICAL TO',0x2264:'LESS-THAN OR EQUAL TO',0x2265:'GREATER-THAN OR EQUAL TO',
  0x2295:'CIRCLED PLUS',0x2296:'CIRCLED MINUS',0x2297:'CIRCLED TIMES',
  0x2299:'CIRCLED DOT OPERATOR',0x22A2:'RIGHT TACK',0x22A3:'LEFT TACK',
  0x22A4:'DOWN TACK',0x22A5:'UP TACK',0x22BB:'XOR',0x22BC:'NAND',
  0x25B3:'WHITE UP-POINTING TRIANGLE',0x25BD:'WHITE DOWN-POINTING TRIANGLE',
  0x2026:'HORIZONTAL ELLIPSIS',0x2032:'PRIME',0x2033:'DOUBLE PRIME',
  0x2034:'TRIPLE PRIME',0x2044:'FRACTION SLASH',0x2118:'SCRIPT CAPITAL P',
  0x2135:'ALEF SYMBOL',0x2153:'VULGAR FRACTION ONE THIRD',
  0x2154:'VULGAR FRACTION TWO THIRDS',0x2155:'VULGAR FRACTION ONE FIFTH',
  0x2189:'VULGAR FRACTION ZERO THIRDS',0x00B1:'PLUS-MINUS SIGN',
  0x00B2:'SUPERSCRIPT TWO',0x00B3:'SUPERSCRIPT THREE',0x00B9:'SUPERSCRIPT ONE',
  0x00BC:'VULGAR FRACTION ONE QUARTER',0x00BD:'VULGAR FRACTION ONE HALF',
  0x00BE:'VULGAR FRACTION THREE QUARTERS',0x00D7:'MULTIPLICATION SIGN',0x00F7:'DIVISION SIGN',
};

// Box Drawing (0x2500–0x257F)
const boxNames = {};
const boxLabels = [
  'LIGHT HORIZONTAL','HEAVY HORIZONTAL','LIGHT VERTICAL','HEAVY VERTICAL',
  'LIGHT TRIPLE DASH HORIZONTAL','HEAVY TRIPLE DASH HORIZONTAL',
  'LIGHT TRIPLE DASH VERTICAL','HEAVY TRIPLE DASH VERTICAL',
  'LIGHT QUADRUPLE DASH HORIZONTAL','HEAVY QUADRUPLE DASH HORIZONTAL',
  'LIGHT QUADRUPLE DASH VERTICAL','HEAVY QUADRUPLE DASH VERTICAL',
  'LIGHT DOWN AND RIGHT','HEAVY DOWN AND RIGHT',
  'DOWN LIGHT AND RIGHT HEAVY','DOWN HEAVY AND RIGHT LIGHT',
  'HEAVY DOWN AND RIGHT','LIGHT DOWN AND LEFT','HEAVY DOWN AND LEFT',
  'DOWN LIGHT AND LEFT HEAVY','DOWN HEAVY AND LEFT LIGHT',
  'HEAVY DOWN AND LEFT','LIGHT UP AND RIGHT','HEAVY UP AND RIGHT',
  'UP LIGHT AND RIGHT HEAVY','UP HEAVY AND RIGHT LIGHT',
  'HEAVY UP AND RIGHT','LIGHT UP AND LEFT','HEAVY UP AND LEFT',
  'UP LIGHT AND LEFT HEAVY','UP HEAVY AND LEFT LIGHT','HEAVY UP AND LEFT',
  'LIGHT VERTICAL AND RIGHT','HEAVY VERTICAL AND RIGHT',
  'VERTICAL LIGHT AND RIGHT HEAVY','UP HEAVY AND RIGHT DOWN LIGHT',
  'DOWN HEAVY AND RIGHT UP LIGHT','HEAVY VERTICAL AND RIGHT',
  'LIGHT VERTICAL AND LEFT','HEAVY VERTICAL AND LEFT',
  'VERTICAL LIGHT AND LEFT HEAVY','UP HEAVY AND LEFT DOWN LIGHT',
  'DOWN HEAVY AND LEFT UP LIGHT','HEAVY VERTICAL AND LEFT',
  'LIGHT DOWN AND HORIZONTAL','HEAVY DOWN AND HORIZONTAL',
  'DOWN LIGHT AND HORIZONTAL HEAVY','DOWN HEAVY AND HORIZONTAL LIGHT',
  'HEAVY DOWN AND HORIZONTAL','LIGHT UP AND HORIZONTAL',
  'HEAVY UP AND HORIZONTAL','UP LIGHT AND HORIZONTAL HEAVY',
  'UP HEAVY AND HORIZONTAL LIGHT','HEAVY UP AND HORIZONTAL',
  'LIGHT VERTICAL AND HORIZONTAL','HEAVY VERTICAL AND HORIZONTAL',
  'VERTICAL LIGHT AND HORIZONTAL HEAVY','VERTICAL HEAVY AND HORIZONTAL LIGHT',
  'HEAVY VERTICAL AND HORIZONTAL','LIGHT DOUBLE DASH HORIZONTAL',
  'HEAVY DOUBLE DASH HORIZONTAL','LIGHT DOUBLE DASH VERTICAL',
  'HEAVY DOUBLE DASH VERTICAL','DOUBLE HORIZONTAL','DOUBLE VERTICAL',
  'DOWN SINGLE AND RIGHT DOUBLE','DOWN DOUBLE AND RIGHT SINGLE',
  'DOUBLE DOWN AND RIGHT','DOWN SINGLE AND LEFT DOUBLE',
  'DOWN DOUBLE AND LEFT SINGLE','DOUBLE DOWN AND LEFT',
  'UP SINGLE AND RIGHT DOUBLE','UP DOUBLE AND RIGHT SINGLE',
  'DOUBLE UP AND RIGHT','UP SINGLE AND LEFT DOUBLE',
  'UP DOUBLE AND LEFT SINGLE','DOUBLE UP AND LEFT',
  'VERTICAL SINGLE AND RIGHT DOUBLE','VERTICAL DOUBLE AND RIGHT SINGLE',
  'DOUBLE VERTICAL AND RIGHT','VERTICAL SINGLE AND LEFT DOUBLE',
  'VERTICAL DOUBLE AND LEFT SINGLE','DOUBLE VERTICAL AND LEFT',
  'DOWN SINGLE AND HORIZONTAL DOUBLE','DOWN DOUBLE AND HORIZONTAL SINGLE',
  'DOUBLE DOWN AND HORIZONTAL','UP SINGLE AND HORIZONTAL DOUBLE',
  'UP DOUBLE AND HORIZONTAL SINGLE','DOUBLE UP AND HORIZONTAL',
  'VERTICAL SINGLE AND HORIZONTAL DOUBLE','VERTICAL DOUBLE AND HORIZONTAL SINGLE',
  'DOUBLE VERTICAL AND HORIZONTAL',
  'LIGHT ARC DOWN AND RIGHT','LIGHT ARC DOWN AND LEFT',
  'LIGHT ARC UP AND LEFT','LIGHT ARC UP AND RIGHT',
  'LIGHT DIAGONAL UPPER RIGHT TO LOWER LEFT',
  'LIGHT DIAGONAL UPPER LEFT TO LOWER RIGHT',
  'LIGHT DIAGONAL CROSS','LIGHT LEFT','LIGHT UP','LIGHT RIGHT','LIGHT DOWN',
  'HEAVY LEFT','HEAVY UP','HEAVY RIGHT','HEAVY DOWN',
  'LIGHT LEFT AND HEAVY RIGHT','LIGHT UP AND HEAVY DOWN',
  'HEAVY LEFT AND LIGHT RIGHT','HEAVY UP AND LIGHT DOWN',
];
for (let i = 0; i < 0x80 && i < boxLabels.length; i++) {
  boxNames[0x2500 + i] = 'BOX DRAWINGS ' + boxLabels[i];
}

// Currency
const currencyNames = {
  0x24:'DOLLAR SIGN',0xA2:'CENT SIGN',0xA3:'POUND SIGN',0xA4:'CURRENCY SIGN',
  0xA5:'YEN SIGN',0x20A0:'EURO-CURRENCY SIGN',0x20A1:'COLON SIGN',
  0x20A2:'CRUZEIRO SIGN',0x20A3:'FRENCH FRANC SIGN',0x20A4:'LIRA SIGN',
  0x20A5:'MILL SIGN',0x20A6:'NAIRA SIGN',0x20A7:'PESETA SIGN',
  0x20A8:'RUPEE SIGN',0x20A9:'WON SIGN',0x20AA:'NEW SHEQEL SIGN',
  0x20AB:'DONG SIGN',0x20AC:'EURO SIGN',0x20AD:'KIP SIGN',
  0x20AE:'TUGRIK SIGN',0x20AF:'DRACHMA SIGN',0x20B0:'GERMAN PENNY SIGN',
  0x20B1:'PESO SIGN',0x20B2:'GUARANI SIGN',0x20B3:'AUSTRAL SIGN',
  0x20B4:'HRYVNIA SIGN',0x20B5:'CEDI SIGN',0x20B6:'LIVRE TOURNOIS SIGN',
  0x20B7:'SPESMILO SIGN',0x20B8:'TENGE SIGN',0x20B9:'INDIAN RUPEE SIGN',
  0x20BA:'TURKISH LIRA SIGN',0x20BB:'NORDIC MARK SIGN',0x20BC:'MANAT SIGN',
  0x20BD:'RUBLE SIGN',0x20BE:'LARI SIGN',0x20BF:'BITCOIN SIGN',
  0x20C0:'SOM SIGN',
};

// Dingbats (selected from U+2700–U+27BF and common symbols)
const dingbatNames = {
  0x2600:'BLACK SUN WITH RAYS',0x2601:'CLOUD',0x2602:'UMBRELLA',
  0x2603:'SNOWMAN',0x2604:'COMET',0x2605:'BLACK STAR',0x2606:'WHITE STAR',
  0x2607:'LIGHTNING',0x2608:'THUNDERSTORM',0x2609:'SUN',
  0x260A:'ASCENDING NODE',0x260B:'DESCENDING NODE',0x260C:'CONJUNCTION',
  0x260D:'OPPOSITION',0x260E:'BLACK TELEPHONE',0x260F:'WHITE TELEPHONE',
  0x2610:'BALLOT BOX',0x2611:'BALLOT BOX WITH CHECK',0x2612:'BALLOT BOX WITH X',
  0x2613:'SALTIRE',0x2614:'UMBRELLA WITH RAIN DROPS',
  0x2615:'HOT BEVERAGE',0x2616:'WHITE SHOGI PIECE',0x2617:'BLACK SHOGI PIECE',
  0x2618:'SHAMROCK',0x2619:'REVERSED ROTATED FLORAL HEART BULLET',
  0x261A:'BLACK LEFT POINTING INDEX',0x261B:'BLACK RIGHT POINTING INDEX',
  0x261C:'WHITE LEFT POINTING INDEX',0x261D:'WHITE UP POINTING INDEX',
  0x261E:'WHITE RIGHT POINTING INDEX',0x261F:'WHITE DOWN POINTING INDEX',
  0x2620:'SKULL AND CROSSBONES',0x2621:'CAUTION SIGN',0x2622:'RADIOACTIVE SIGN',
  0x2623:'BIOHAZARD SIGN',0x2624:'CADUCEUS',0x2625:'ANKH',
  0x2626:'ORTHODOX CROSS',0x2627:'CHI RHO',0x2628:'CROSS OF LORRAINE',
  0x2629:'CROSS OF JERUSALEM',0x262A:'STAR AND CRESCENT',
  0x262B:'FARSI SYMBOL',0x262C:'ADI SHAKTI',0x262D:'HAMMER AND SICKLE',
  0x262E:'PEACE SYMBOL',0x262F:'YIN YANG',
  0x2630:'TRIGRAM FOR HEAVEN',0x2631:'TRIGRAM FOR LAKE',
  0x2632:'TRIGRAM FOR FIRE',0x2633:'TRIGRAM FOR THUNDER',
  0x2634:'TRIGRAM FOR WIND',0x2635:'TRIGRAM FOR WATER',
  0x2636:'TRIGRAM FOR MOUNTAIN',0x2637:'TRIGRAM FOR EARTH',
  0x2638:'WHEEL OF DHARMA',0x2639:'WHITE FROWNING FACE',
  0x263A:'WHITE SMILING FACE',0x263B:'BLACK SMILING FACE',
  0x263C:'WHITE SUN WITH RAYS',0x263D:'FIRST QUARTER MOON',
  0x263E:'LAST QUARTER MOON',0x263F:'MERCURY',
  0x2640:'FEMALE SIGN',0x2641:'EARTH',0x2642:'MALE SIGN',
  0x2643:'JUPITER',0x2644:'SATURN',0x2645:'URANUS',0x2646:'NEPTUNE',
  0x2647:'PLUTO',0x2648:'ARIES',0x2649:'TAURUS',0x264A:'GEMINI',
  0x264B:'CANCER',0x264C:'LEO',0x264D:'VIRGO',0x264E:'LIBRA',
  0x264F:'SCORPIUS',0x2650:'SAGITTARIUS',0x2651:'CAPRICORN',
  0x2652:'AQUARIUS',0x2653:'PISCES',0x2654:'WHITE CHESS KING',
  0x2655:'WHITE CHESS QUEEN',0x2656:'WHITE CHESS ROOK',
  0x2657:'WHITE CHESS BISHOP',0x2658:'WHITE CHESS KNIGHT',
  0x2659:'WHITE CHESS PAWN',0x265A:'BLACK CHESS KING',
  0x265B:'BLACK CHESS QUEEN',0x265C:'BLACK CHESS ROOK',
  0x265D:'BLACK CHESS BISHOP',0x265E:'BLACK CHESS KNIGHT',
  0x265F:'BLACK CHESS PAWN',0x2660:'BLACK SPADE SUIT',
  0x2661:'WHITE HEART SUIT',0x2662:'WHITE DIAMOND SUIT',
  0x2663:'BLACK CLUB SUIT',0x2664:'WHITE SPADE SUIT',
  0x2665:'BLACK HEART SUIT',0x2666:'BLACK DIAMOND SUIT',
  0x2667:'WHITE CLUB SUIT',0x2668:'HOT SPRINGS',0x2669:'QUARTER NOTE',
  0x266A:'EIGHTH NOTE',0x266B:'BEAMED EIGHTH NOTES',
  0x266C:'BEAMED SIXTEENTH NOTES',0x266D:'MUSIC FLAT SIGN',
  0x266E:'MUSIC NATURAL SIGN',0x266F:'MUSIC SHARP SIGN',
  0x2670:'WEST SYRIAC CROSS',0x2671:'EAST SYRIAC CROSS',
  0x2672:'UNIVERSAL RECYCLING SYMBOL',0x2673:'RECYCLING SYMBOL FOR TYPE-1 PLASTICS',
  0x2674:'RECYCLING SYMBOL FOR TYPE-2 PLASTICS',0x2675:'RECYCLING SYMBOL FOR TYPE-3 PLASTICS',
  0x267B:'BLACK UNIVERSAL RECYCLING SYMBOL',0x267C:'RECYCLED PAPER SYMBOL',
  0x267E:'PERMANENT PAPER SIGN',0x267F:'WHEELCHAIR SYMBOL',
  0x2680:'DIE FACE-1',0x2681:'DIE FACE-2',0x2682:'DIE FACE-3',
  0x2683:'DIE FACE-4',0x2684:'DIE FACE-5',0x2685:'DIE FACE-6',
  0x2686:'WHITE CIRCLE WITH DOT RIGHT',0x2687:'WHITE CIRCLE WITH TWO DOTS',
  0x2688:'BLACK CIRCLE WITH WHITE DOT RIGHT',0x2689:'BLACK CIRCLE WITH TWO WHITE DOTS',
  0x2702:'BLACK SCISSORS',0x2703:'WHITE SCISSORS',0x2704:'SCISSORS',
  0x2706:'TELEPHONE LOCATION SIGN',0x2707:'TAPE DRIVE',
  0x2708:'AIRPLANE',0x2709:'ENVELOPE',0x270A:'RAISED FIST',
  0x270B:'RAISED HAND',0x270C:'VICTORY HAND',0x270D:'WRITING HAND',
  0x270E:'LOWER RIGHT PENCIL',0x270F:'PENCIL',0x2710:'UPPER RIGHT PENCIL',
  0x2711:'WHITE NIB',0x2712:'BLACK NIB',0x2713:'CHECK MARK',
  0x2714:'HEAVY CHECK MARK',0x2715:'MULTIPLICATION X',0x2716:'HEAVY MULTIPLICATION X',
  0x2717:'BALLOT X',0x2718:'HEAVY BALLOT X',0x2719:'OUTLINED GREEK CROSS',
  0x271A:'HEAVY GREEK CROSS',0x271B:'OPEN CENTRE CROSS',0x271C:'HEAVY OPEN CENTRE CROSS',
  0x271D:'LATIN CROSS',0x271E:'SHADOWED WHITE LATIN CROSS',0x271F:'OUTLINED LATIN CROSS',
  0x2720:'MALTESE CROSS',0x2721:'STAR OF DAVID',0x2722:'FOUR TEARDROP-SPOKED ASTERISK',
  0x2723:'FOUR BALLOON-SPOKED ASTERISK',0x2724:'HEAVY FOUR BALLOON-SPOKED ASTERISK',
  0x2725:'FOUR CLUB-SPOKED ASTERISK',0x2726:'BLACK FOUR POINTED STAR',
  0x2727:'WHITE FOUR POINTED STAR',0x2728:'SPARKLES',0x2729:'STRESS OUTLINED WHITE STAR',
  0x272A:'CIRCLED WHITE STAR',0x272B:'OPEN CENTRE BLACK STAR',
  0x272C:'BLACK CENTRE WHITE STAR',0x272D:'OUTLINED BLACK STAR',
  0x272E:'HEAVY OUTLINED BLACK STAR',0x272F:'PINWHEEL STAR',
  0x2730:'SHADOWED WHITE STAR',0x2731:'HEAVY ASTERISK',0x2732:'OPEN CENTRE ASTERISK',
  0x2733:'EIGHT SPOKED ASTERISK',0x2734:'EIGHT POINTED BLACK STAR',
  0x2735:'EIGHT POINTED PINWHEEL STAR',0x2736:'SIX POINTED BLACK STAR',
  0x2737:'EIGHT POINTED RECTILINEAR BLACK STAR',0x2738:'HEAVY EIGHT POINTED RECTILINEAR BLACK STAR',
  0x2739:'TWELVE POINTED BLACK STAR',0x273A:'SIXTEEN POINTED ASTERISK',
  0x273B:'TEARDROP-SPOKED ASTERISK',0x273C:'OPEN CENTRE TEARDROP-SPOKED ASTERISK',
  0x273D:'HEAVY TEARDROP-SPOKED ASTERISK',0x273E:'SIX PETALLED BLACK AND WHITE FLORETTE',
  0x273F:'BLACK FLORETTE',0x2740:'WHITE FLORETTE',0x2741:'EIGHT PETALLED OUTLINED BLACK FLORETTE',
  0x2742:'CIRCLED OPEN CENTRE EIGHT POINTED STAR',0x2743:'HEAVY TEARDROP-SPOKED PINWHEEL ASTERISK',
  0x2744:'SNOWFLAKE',0x2745:'TIGHT TRIFOLIATE SNOWFLAKE',0x2746:'HEAVY CHEVRON SNOWFLAKE',
  0x2747:'SPARKLE',0x2748:'HEAVY SPARKLE',0x2749:'BALLOON-SPOKED ASTERISK',
  0x274A:'EIGHT TEARDROP-SPOKED PROPELLER ASTERISK',
  0x274B:'HEAVY EIGHT TEARDROP-SPOKED PROPELLER ASTERISK',
  0x274D:'SHADOWED WHITE CIRCLE',0x274F:'LOWER RIGHT DROP-SHADOWED WHITE SQUARE',
  0x2750:'UPPER RIGHT DROP-SHADOWED WHITE SQUARE',0x2751:'LOWER RIGHT SHADOWED WHITE SQUARE',
  0x2752:'UPPER RIGHT SHADOWED WHITE SQUARE',0x2756:'BLACK DIAMOND MINUS WHITE X',
  0x2757:'HEAVY EXCLAMATION MARK ORNAMENT',0x2763:'HEAVY HEART EXCLAMATION MARK ORNAMENT',
  0x2764:'HEAVY BLACK HEART',0x2765:'ROTATED HEAVY BLACK HEART BULLET',
  0x2766:'FLORAL HEART',0x2767:'ROTATED FLORAL HEART BULLET',
  0x2794:'HEAVY WIDE-HEADED RIGHTWARDS ARROW',
  0x2798:'HEAVY SOUTH EAST ARROW',0x2799:'HEAVY RIGHTWARDS ARROW',
  0x279A:'HEAVY NORTH EAST ARROW',0x279B:'DRAFTING POINT RIGHTWARDS ARROW',
  0x279C:'HEAVY ROUND-TIPPED RIGHTWARDS ARROW',0x279D:'TRIANGLE-HEADED RIGHTWARDS ARROW',
  0x279E:'HEAVY TRIANGLE-HEADED RIGHTWARDS ARROW',0x279F:'DASHED TRIANGLE-HEADED RIGHTWARDS ARROW',
  0x27A0:'HEAVY DASHED TRIANGLE-HEADED RIGHTWARDS ARROW',0x27A1:'BLACK RIGHTWARDS ARROW',
  0x27B0:'CURLY LOOP',0x27B2:'CAUTION SIGN',0x27B3:'WHITE FEATHERED RIGHT ARROW HEAD',
};

/* ── Build category lists ── */
const CAT_DATA = {
  latin:     Object.keys(latinNames).map(k=>({cp:+k, name:latinNames[k]})),
  'latin-ext': Object.keys(latinExtNames).map(k=>({cp:+k, name:latinExtNames[k]})),
  greek:     Object.keys(greekNames).map(k=>({cp:+k, name:greekNames[k]})),
  cyrillic:  Object.keys(cyrillicNames).map(k=>({cp:+k, name:cyrillicNames[k]})),
  arrows:    Object.keys(arrowNames).map(k=>({cp:+k, name:arrowNames[k]})),
  math:      Object.keys(mathNames).map(k=>({cp:+k, name:mathNames[k]})),
  box:       Object.keys(boxNames).map(k=>({cp:+k, name:boxNames[k]})),
  currency:  Object.keys(currencyNames).map(k=>({cp:+k, name:currencyNames[k]})),
  dingbats:  Object.keys(dingbatNames).map(k=>({cp:+k, name:dingbatNames[k]})),
};

/* ── UTF-8 encoder ── */
function toUtf8Hex(cp) {
  const bytes = [];
  if (cp < 0x80) {
    bytes.push(cp);
  } else if (cp < 0x800) {
    bytes.push(0xC0 | (cp >> 6), 0x80 | (cp & 0x3F));
  } else if (cp < 0x10000) {
    bytes.push(0xE0 | (cp >> 12), 0x80 | ((cp >> 6) & 0x3F), 0x80 | (cp & 0x3F));
  } else {
    bytes.push(
      0xF0 | (cp >> 18),
      0x80 | ((cp >> 12) & 0x3F),
      0x80 | ((cp >> 6) & 0x3F),
      0x80 | (cp & 0x3F)
    );
  }
  return bytes.map(b => b.toString(16).toUpperCase().padStart(2,'0')).join(' ');
}

/* ── HTML entity ── */
const NAMED_ENTITIES = {
  0x22:'&quot;',0x26:'&amp;',0x27:'&apos;',0x3C:'&lt;',0x3E:'&gt;',
  0xA0:'&nbsp;',0xA9:'&copy;',0xAE:'&reg;',0x2122:'&trade;',
  0xA3:'&pound;',0xA5:'&yen;',0xA2:'&cent;',0x20AC:'&euro;',
  0xB1:'&plusmn;',0xD7:'&times;',0xF7:'&divide;',
  0x221E:'&infin;',0x2248:'&asymp;',0x2260:'&ne;',
  0x2264:'&le;',0x2265:'&ge;',0x2190:'&larr;',0x2191:'&uarr;',
  0x2192:'&rarr;',0x2193:'&darr;',0x2194:'&harr;',0x21D4:'&hArr;',
  0x2665:'&hearts;',0x2666:'&diams;',0x2663:'&clubs;',0x2660:'&spades;',
};

function htmlEntity(cp) {
  if (NAMED_ENTITIES[cp]) return NAMED_ENTITIES[cp];
  return '&#' + cp + ';';
}

function cpToChar(cp) {
  return cp > 0xFFFF
    ? String.fromCodePoint(cp)
    : String.fromCharCode(cp);
}

function cpHex(cp) {
  return 'U+' + cp.toString(16).toUpperCase().padStart(4,'0');
}

function cssContent(cp) {
  return '"\\' + cp.toString(16).toUpperCase() + '"';
}

/* ── State ── */
let currentCat = 'arrows';
let searchQuery = '';
let selectedChar = null;
const RECENT_KEY = 'cm_recent_v1';

function getRecent() {
  try { return JSON.parse(localStorage.getItem(RECENT_KEY) || '[]'); } catch(e) { return []; }
}
function addRecent(cp, name) {
  let arr = getRecent().filter(x => x.cp !== cp);
  arr.unshift({cp, name});
  if (arr.length > 20) arr = arr.slice(0, 20);
  try { localStorage.setItem(RECENT_KEY, JSON.stringify(arr)); } catch(e) {}
}

/* ── Copy ── */
let toastTimer;
function copyText(text, label) {
  const fallback = () => {
    const ta = document.createElement('textarea');
    ta.value = text;
    ta.style.cssText = 'position:fixed;opacity:0;top:0;left:0';
    document.body.appendChild(ta);
    ta.select();
    document.execCommand('copy');
    ta.remove();
  };
  if (navigator.clipboard && window.isSecureContext) {
    navigator.clipboard.writeText(text).catch(fallback);
  } else { fallback(); }
  showToast('Copied: ' + label);
}

function showToast(msg) {
  const t = document.getElementById('cm-toast');
  t.textContent = msg;
  t.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(() => t.classList.remove('show'), 2000);
}

/* ── Render ── */
function getChars() {
  if (searchQuery.length >= 2) {
    const q = searchQuery.toLowerCase();
    const all = [];
    for (const cat of CATS) {
      for (const ch of CAT_DATA[cat.id]) {
        if (ch.name.toLowerCase().includes(q)) {
          all.push(ch);
        }
      }
    }
    return all;
  }
  return CAT_DATA[currentCat] || [];
}

function renderGrid() {
  const grid = document.getElementById('cm-grid');
  const chars = getChars();
  if (!chars.length) {
    grid.innerHTML = '<div class="cm-empty">No characters found. Try a different search term.</div>';
    return;
  }
  grid.innerHTML = chars.map(ch => {
    const char = cpToChar(ch.cp);
    const hex = cpHex(ch.cp);
    const tipName = ch.name || hex;
    return `<div class="cm-cell" data-cp="${ch.cp}" title="${tipName}" role="button" tabindex="0" aria-label="${tipName}">
      ${char}
      <span class="cm-tip">${tipName}<br><small>${hex}</small></span>
    </div>`;
  }).join('');

  grid.querySelectorAll('.cm-cell').forEach(el => {
    el.addEventListener('click', () => selectChar(+el.dataset.cp, chars.find(c=>c.cp===+el.dataset.cp)?.name||''));
    el.addEventListener('keydown', e => { if (e.key==='Enter'||e.key===' ') selectChar(+el.dataset.cp, chars.find(c=>c.cp===+el.dataset.cp)?.name||''); });
  });
}

function selectChar(cp, name) {
  selectedChar = {cp, name};
  addRecent(cp, name);
  renderRecent();

  const char = cpToChar(cp);
  copyText(char, char + ' ' + cpHex(cp));

  // Detail panel
  document.getElementById('cm-detail-char').textContent = char;
  document.getElementById('cm-detail-name').textContent = name || cpHex(cp);

  const fields = [
    { label:'Code Point', val: cpHex(cp) },
    { label:'HTML Entity', val: htmlEntity(cp) },
    { label:'CSS content', val: cssContent(cp) },
    { label:'UTF-8 Hex', val: toUtf8Hex(cp) },
  ];

  document.getElementById('cm-detail-grid').innerHTML = fields.map(f => `
    <div class="cm-detail-row">
      <span class="cm-detail-label">${f.label}</span>
      <span class="cm-detail-val">${f.val}</span>
      <button class="cm-copy-btn" data-copy="${f.val}">Copy</button>
    </div>
  `).join('');

  document.getElementById('cm-detail-grid').querySelectorAll('.cm-copy-btn').forEach(btn => {
    btn.addEventListener('click', e => {
      e.stopPropagation();
      copyText(btn.dataset.copy, btn.dataset.copy);
    });
  });

  document.getElementById('cm-detail').classList.add('visible');
}

function renderTabs() {
  const tabs = document.getElementById('cm-tabs');
  tabs.innerHTML = CATS.map(c =>
    `<button class="cm-tab${c.id===currentCat?' active':''}" data-cat="${c.id}">${c.label}</button>`
  ).join('');
  tabs.querySelectorAll('.cm-tab').forEach(btn => {
    btn.addEventListener('click', () => {
      currentCat = btn.dataset.cat;
      searchQuery = '';
      document.getElementById('cm-search').value = '';
      document.getElementById('cm-detail').classList.remove('visible');
      renderTabs();
      renderGrid();
    });
  });
}

function renderRecent() {
  const recent = getRecent();
  const sec = document.getElementById('cm-recent-section');
  const row = document.getElementById('cm-recent-row');
  if (!recent.length) { sec.style.display='none'; return; }
  sec.style.display = 'block';
  row.innerHTML = recent.map(r => {
    const char = cpToChar(r.cp);
    const hex = cpHex(r.cp);
    return `<div class="cm-recent-chip" data-cp="${r.cp}" title="${r.name||hex}" role="button" tabindex="0">
      ${char}<span class="chip-label">${hex}</span>
    </div>`;
  }).join('');
  row.querySelectorAll('.cm-recent-chip').forEach(el => {
    el.addEventListener('click', () => {
      const cp = +el.dataset.cp;
      const name = getRecent().find(x=>x.cp===cp)?.name||'';
      selectChar(cp, name);
    });
  });
}

/* ── Search ── */
document.getElementById('cm-search').addEventListener('input', function() {
  searchQuery = this.value.trim();
  document.getElementById('cm-detail').classList.remove('visible');
  // Deactivate tabs when searching
  document.querySelectorAll('#cm-tabs .cm-tab').forEach(t => t.classList.remove('active'));
  if (!searchQuery) {
    document.querySelectorAll('#cm-tabs .cm-tab').forEach(t => {
      if (t.dataset.cat === currentCat) t.classList.add('active');
    });
  }
  renderGrid();
});

/* ── Init ── */
renderTabs();
renderRecent();
renderGrid();

})();
</script>

---
### Related Tools
> Search emoji → [Emoji Search](/tools/emoji-search/)
> Encode HTML entities → [HTML Entity Encoder](/tools/html-entity-encoder/)

</div>
