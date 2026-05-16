---
title: "オープンソースライセンス選択ツール"
slug: "license-chooser"
date: 2025-05-16
description: "無料のオープンソースライセンス選択ツール。MIT・Apache・GPL・BSDなど主要ライセンスを比較し、質問に答えてプロジェクトに最適なライセンスを選択。"
categories: ["無料ツール"]
tags: ["オープンソース", "ライセンス", "MIT", "Apache", "GPL", "BSD", "開発者ツール"]
ShowToc: false
cover:
  image: "/images/covers/license-chooser-ja.png"
  alt: "オープンソースライセンス選択ツール"
---

OSSプロジェクトに最適なライセンスを選ぶ無料ツール。質問に答えるだけでおすすめライセンスを提案。主要ライセンスを一覧比較し、名前・年を入力してライセンス文書をそのままコピーできます。

**関連ツール:** [Gitコマンドジェネレーター](/ja/tools/git-command-generator/) &mdash; [変更履歴ジェネレーター](/ja/tools/changelog-generator/)

<div id="ol-app">

<style>
#ol-app {
  font-family: -apple-system, BlinkMacSystemFont, "Hiragino Kaku Gothic ProN", "Noto Sans JP", "Segoe UI", sans-serif;
  max-width: 900px;
  margin: 0 auto;
  color: #1a1a2e;
}
#ol-app * { box-sizing: border-box; }

/* Tabs */
#ol-app .ol-tabs {
  display: flex;
  gap: 4px;
  margin-bottom: 24px;
  border-bottom: 2px solid #e2e8f0;
}
#ol-app .ol-tab-btn {
  padding: 10px 22px;
  border: none;
  background: none;
  cursor: pointer;
  font-size: 15px;
  font-weight: 700;
  color: #64748b;
  border-bottom: 3px solid transparent;
  margin-bottom: -2px;
  transition: color 0.2s, border-color 0.2s;
}
#ol-app .ol-tab-btn.active {
  color: #4f46e5;
  border-bottom-color: #4f46e5;
}
#ol-app .ol-tab-btn:hover:not(.active) { color: #334155; }

/* Panel */
#ol-app .ol-panel { display: none; }
#ol-app .ol-panel.active { display: block; }

/* Wizard */
#ol-app .ol-wizard-step {
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 28px;
  margin-bottom: 20px;
}
#ol-app .ol-wizard-step h3 { margin: 0 0 8px; font-size: 17px; color: #1e293b; }
#ol-app .ol-wizard-step p { margin: 0 0 16px; color: #64748b; font-size: 14px; }
#ol-app .ol-btn-group { display: flex; gap: 10px; flex-wrap: wrap; }
#ol-app .ol-choice-btn {
  padding: 10px 20px;
  border: 2px solid #e2e8f0;
  border-radius: 8px;
  background: #fff;
  cursor: pointer;
  font-size: 14px;
  font-weight: 500;
  color: #334155;
  transition: all 0.15s;
}
#ol-app .ol-choice-btn:hover { border-color: #4f46e5; color: #4f46e5; }
#ol-app .ol-choice-btn.selected { border-color: #4f46e5; background: #eef2ff; color: #4f46e5; }

#ol-app .ol-step-indicator { display: flex; align-items: center; gap: 8px; margin-bottom: 24px; }
#ol-app .ol-step-dot {
  width: 28px; height: 28px;
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: 12px; font-weight: 700;
  background: #e2e8f0; color: #64748b;
  transition: all 0.2s;
}
#ol-app .ol-step-dot.done { background: #4f46e5; color: #fff; }
#ol-app .ol-step-dot.current { background: #818cf8; color: #fff; }
#ol-app .ol-step-line { flex: 1; height: 2px; background: #e2e8f0; }
#ol-app .ol-step-line.done { background: #4f46e5; }

#ol-app .ol-result-box {
  border: 2px solid #4f46e5;
  border-radius: 12px;
  padding: 28px;
  background: #eef2ff;
  margin-top: 24px;
}
#ol-app .ol-result-box h3 { margin: 0 0 6px; color: #4f46e5; font-size: 20px; }
#ol-app .ol-result-box .ol-tldr { font-size: 14px; color: #334155; margin-bottom: 16px; }
#ol-app .ol-result-actions { display: flex; gap: 10px; flex-wrap: wrap; margin-top: 16px; }
#ol-app .ol-btn-primary {
  padding: 10px 20px; background: #4f46e5; color: #fff;
  border: none; border-radius: 8px;
  cursor: pointer; font-size: 14px; font-weight: 700;
  transition: background 0.2s;
}
#ol-app .ol-btn-primary:hover { background: #4338ca; }
#ol-app .ol-btn-secondary {
  padding: 10px 20px; background: #fff; color: #4f46e5;
  border: 2px solid #4f46e5; border-radius: 8px;
  cursor: pointer; font-size: 14px; font-weight: 700;
  transition: all 0.2s;
}
#ol-app .ol-btn-secondary:hover { background: #eef2ff; }

/* Comparison table */
#ol-app .ol-table-wrap { overflow-x: auto; }
#ol-app .ol-table { width: 100%; border-collapse: collapse; font-size: 13px; }
#ol-app .ol-table th {
  background: #1e293b; color: #fff;
  padding: 10px 14px; text-align: left;
  white-space: nowrap; position: sticky; top: 0;
}
#ol-app .ol-table td { padding: 9px 14px; border-bottom: 1px solid #e2e8f0; vertical-align: top; }
#ol-app .ol-table tr:hover td { background: #f8fafc; }
#ol-app .ol-table .ol-license-name {
  font-weight: 700; color: #4f46e5; cursor: pointer; white-space: nowrap;
}
#ol-app .ol-table .ol-license-name:hover { text-decoration: underline; }
#ol-app .ol-check { color: #16a34a; font-weight: 700; }
#ol-app .ol-cross { color: #dc2626; font-weight: 700; }

/* Badge */
#ol-app .ol-badge {
  display: inline-block; padding: 2px 10px; border-radius: 4px;
  font-size: 11px; font-weight: 700; letter-spacing: 0.02em;
}
#ol-app .ol-badge-permissive { background: #dcfce7; color: #15803d; }
#ol-app .ol-badge-copyleft   { background: #fee2e2; color: #b91c1c; }
#ol-app .ol-badge-weak       { background: #fef3c7; color: #92400e; }
#ol-app .ol-badge-public     { background: #e0e7ff; color: #3730a3; }

/* Shield */
#ol-app .ol-shields-row { display: flex; align-items: center; gap: 10px; flex-wrap: wrap; margin-top: 12px; }
#ol-app .ol-shield {
  display: inline-flex; align-items: center;
  border-radius: 4px; overflow: hidden;
  font-size: 11px; font-weight: 600; height: 20px;
}
#ol-app .ol-shield-left { background: #555; color: #fff; padding: 0 6px; }
#ol-app .ol-shield-right { padding: 0 8px; color: #fff; }

/* Modal */
#ol-app .ol-modal-backdrop {
  display: none; position: fixed; inset: 0;
  background: rgba(0,0,0,0.5);
  z-index: 1000; align-items: center; justify-content: center;
}
#ol-app .ol-modal-backdrop.open { display: flex; }
#ol-app .ol-modal {
  background: #fff; border-radius: 14px;
  max-width: 680px; width: 95vw; max-height: 85vh;
  overflow-y: auto; padding: 32px; position: relative;
  box-shadow: 0 20px 60px rgba(0,0,0,0.2);
}
#ol-app .ol-modal-close {
  position: absolute; top: 16px; right: 16px;
  background: #f1f5f9; border: none;
  width: 32px; height: 32px; border-radius: 50%;
  cursor: pointer; font-size: 18px; color: #64748b;
  display: flex; align-items: center; justify-content: center;
}
#ol-app .ol-modal-close:hover { background: #e2e8f0; }
#ol-app .ol-modal h2 { margin: 0 0 4px; font-size: 20px; color: #1e293b; }
#ol-app .ol-modal .ol-modal-tldr { color: #64748b; font-size: 14px; margin-bottom: 20px; }
#ol-app .ol-modal pre {
  background: #0f172a; color: #e2e8f0;
  padding: 20px; border-radius: 10px;
  font-size: 12px; line-height: 1.6;
  white-space: pre-wrap; word-break: break-word;
  max-height: 280px; overflow-y: auto;
}
#ol-app .ol-copy-row { display: flex; gap: 8px; margin-bottom: 14px; flex-wrap: wrap; }
#ol-app .ol-input-sm {
  padding: 7px 10px;
  border: 1px solid #cbd5e1;
  border-radius: 6px; font-size: 13px; width: 160px;
}
#ol-app .ol-copy-btn {
  padding: 7px 16px; background: #4f46e5; color: #fff;
  border: none; border-radius: 6px;
  cursor: pointer; font-size: 13px; font-weight: 700;
  transition: background 0.2s;
}
#ol-app .ol-copy-btn:hover { background: #4338ca; }
#ol-app .ol-copy-btn.copied { background: #16a34a; }
#ol-app .ol-modal-section { margin-bottom: 18px; }
#ol-app .ol-modal-section h4 { font-size: 12px; text-transform: uppercase; letter-spacing: 0.06em; color: #94a3b8; margin: 0 0 8px; }
#ol-app .ol-pill-list { display: flex; flex-wrap: wrap; gap: 6px; }
#ol-app .ol-pill { padding: 3px 10px; border-radius: 20px; font-size: 12px; font-weight: 500; }
#ol-app .ol-pill-green { background: #dcfce7; color: #15803d; }
#ol-app .ol-pill-red   { background: #fee2e2; color: #b91c1c; }
#ol-app .ol-pill-blue  { background: #dbeafe; color: #1d4ed8; }

#ol-app .ol-reset-btn {
  padding: 8px 16px; border: 1px solid #e2e8f0;
  border-radius: 8px; background: #fff; cursor: pointer;
  font-size: 13px; color: #64748b; margin-top: 12px;
}
#ol-app .ol-reset-btn:hover { border-color: #94a3b8; color: #334155; }
</style>

<div class="ol-tabs">
  <button class="ol-tab-btn active" onclick="olSwitchTab('wizard')">ウィザード</button>
  <button class="ol-tab-btn" onclick="olSwitchTab('compare')">ライセンス一覧比較</button>
</div>

<!-- WIZARD PANEL -->
<div id="ol-panel-wizard" class="ol-panel active">
  <div class="ol-step-indicator" id="ol-step-indicator"></div>
  <div id="ol-wizard-body"></div>
</div>

<!-- COMPARE PANEL -->
<div id="ol-panel-compare" class="ol-panel">
  <div class="ol-table-wrap">
    <table class="ol-table" id="ol-compare-table">
      <thead>
        <tr>
          <th>ライセンス</th>
          <th>種別</th>
          <th>商用利用</th>
          <th>改変</th>
          <th>再配布</th>
          <th>特許付与</th>
          <th>私的利用</th>
          <th>コピーレフト</th>
          <th>著作権表示</th>
          <th>ネットワーク配布</th>
        </tr>
      </thead>
      <tbody id="ol-compare-body"></tbody>
    </table>
  </div>
</div>

<!-- MODAL -->
<div class="ol-modal-backdrop" id="ol-modal" onclick="olCloseModal(event)">
  <div class="ol-modal" id="ol-modal-inner">
    <button class="ol-modal-close" onclick="olCloseModal(null, true)">&#10005;</button>
    <div id="ol-modal-content"></div>
  </div>
</div>

<script>
(function() {
"use strict";

var LICENSES = [
  {
    id: "mit",
    name: "MIT",
    fullName: "MIT License",
    type: "permissive",
    badge: "permissive",
    tldr: "シンプルで制約が少ない。著作権表示とライセンス文書の同梱だけが条件。商用利用・改変・再配布すべて自由。最も広く使われている。",
    permissions: ["商用利用","改変","再配布","私的利用"],
    conditions: ["著作権・ライセンス表示の保持"],
    limitations: ["免責（無保証）"],
    commercial: true, modify: true, distribute: true, patent: false, private: true,
    copyleft: false, attribution: true, networkUse: false,
    color: "#16a34a",
    template: `MIT License

Copyright (c) {{YEAR}} {{NAME}}

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.`
  },
  {
    id: "apache2",
    name: "Apache 2.0",
    fullName: "Apache License 2.0",
    type: "permissive",
    badge: "permissive",
    tldr: "MITに特許権の明示的付与と変更箇所の明記義務を加えた許容型。企業プロジェクトに広く採用されている。",
    permissions: ["商用利用","改変","再配布","特許付与","私的利用"],
    conditions: ["著作権・ライセンス表示","変更箇所の明記","NOTICEファイルの保持"],
    limitations: ["免責","商標利用禁止"],
    commercial: true, modify: true, distribute: true, patent: true, private: true,
    copyleft: false, attribution: true, networkUse: false,
    color: "#2563eb",
    template: `Apache License
Version 2.0, January 2004
http://www.apache.org/licenses/

Copyright (c) {{YEAR}} {{NAME}}

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.`
  },
  {
    id: "gplv3",
    name: "GPL v3",
    fullName: "GNU General Public License v3.0",
    type: "copyleft",
    badge: "copyleft",
    tldr: "強いコピーレフト。派生物は同じライセンスで公開必須。特許保護条項・Tivoization対策あり。OSSコミュニティへの還元を重視する場合に適する。",
    permissions: ["商用利用","改変","再配布","特許付与","私的利用"],
    conditions: ["ソース開示","著作権・ライセンス表示","同一ライセンス","変更箇所の明記"],
    limitations: ["免責"],
    commercial: true, modify: true, distribute: true, patent: true, private: true,
    copyleft: true, attribution: true, networkUse: false,
    color: "#dc2626",
    template: `GNU GENERAL PUBLIC LICENSE
Version 3, 29 June 2007

Copyright (C) {{YEAR}} {{NAME}}

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program. If not, see <https://www.gnu.org/licenses/>.`
  },
  {
    id: "gplv2",
    name: "GPL v2",
    fullName: "GNU General Public License v2.0",
    type: "copyleft",
    badge: "copyleft",
    tldr: "古典的な強コピーレフト。Linuxカーネルが採用。特許付与の明示はなし。GPL v3との互換性問題に注意。",
    permissions: ["商用利用","改変","再配布","私的利用"],
    conditions: ["ソース開示","著作権・ライセンス表示","同一ライセンス","変更箇所の明記"],
    limitations: ["免責"],
    commercial: true, modify: true, distribute: true, patent: false, private: true,
    copyleft: true, attribution: true, networkUse: false,
    color: "#b91c1c",
    template: `GNU GENERAL PUBLIC LICENSE
Version 2, June 1991

Copyright (C) {{YEAR}} {{NAME}}

Everyone is permitted to copy and distribute verbatim copies
of this license document, but changing it is not allowed.

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.`
  },
  {
    id: "lgpl",
    name: "LGPL v2.1",
    fullName: "GNU Lesser General Public License v2.1",
    type: "weak-copyleft",
    badge: "weak",
    tldr: "ライブラリ向け弱コピーレフト。ライブラリ本体の改変はオープンにする必要があるが、プロプライエタリなソフトウェアからリンクして使用可能。",
    permissions: ["商用利用","改変","再配布","私的利用"],
    conditions: ["ソース開示（ライブラリ改変分のみ）","著作権・ライセンス表示","同一ライセンス（ライブラリ改変分のみ）"],
    limitations: ["免責"],
    commercial: true, modify: true, distribute: true, patent: false, private: true,
    copyleft: true, attribution: true, networkUse: false,
    color: "#d97706",
    template: `GNU LESSER GENERAL PUBLIC LICENSE
Version 2.1, February 1999

Copyright (C) {{YEAR}} {{NAME}}

This library is free software; you can redistribute it and/or
modify it under the terms of the GNU Lesser General Public
License as published by the Free Software Foundation; either
version 2.1 of the License, or (at your option) any later version.

This library is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
Lesser General Public License for more details.`
  },
  {
    id: "bsd2",
    name: "BSD 2-Clause",
    fullName: 'BSD 2-Clause "Simplified" License',
    type: "permissive",
    badge: "permissive",
    tldr: "シンプルな2条件のみ：ソース配布時とバイナリ配布時の著作権表示。MITとほぼ同等の自由度。",
    permissions: ["商用利用","改変","再配布","私的利用"],
    conditions: ["著作権・ライセンス表示"],
    limitations: ["免責"],
    commercial: true, modify: true, distribute: true, patent: false, private: true,
    copyleft: false, attribution: true, networkUse: false,
    color: "#059669",
    template: `BSD 2-Clause License

Copyright (c) {{YEAR}}, {{NAME}}
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice,
   this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED.`
  },
  {
    id: "bsd3",
    name: "BSD 3-Clause",
    fullName: 'BSD 3-Clause "New" or "Revised" License',
    type: "permissive",
    badge: "permissive",
    tldr: "BSD 2-Clauseに「プロジェクト名・貢献者名を宣伝に使用禁止」の条件を追加。Google・Apple・FreeBSD等が採用。",
    permissions: ["商用利用","改変","再配布","私的利用"],
    conditions: ["著作権・ライセンス表示","名称使用禁止（宣伝目的）"],
    limitations: ["免責"],
    commercial: true, modify: true, distribute: true, patent: false, private: true,
    copyleft: false, attribution: true, networkUse: false,
    color: "#0891b2",
    template: `BSD 3-Clause License

Copyright (c) {{YEAR}}, {{NAME}}
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice,
   this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its contributors
   may be used to endorse or promote products derived from this software
   without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES ARE DISCLAIMED.`
  },
  {
    id: "mpl2",
    name: "MPL 2.0",
    fullName: "Mozilla Public License 2.0",
    type: "weak-copyleft",
    badge: "weak",
    tldr: "ファイル単位の弱コピーレフト。変更したファイルはオープンにする必要があるが、プロプライエタリなコードと組み合わせ可能。MozillaやFirefoxが採用。",
    permissions: ["商用利用","改変","再配布","特許付与","私的利用"],
    conditions: ["ソース開示（変更ファイルのみ）","著作権・ライセンス表示","同一ライセンス（変更ファイルのみ）"],
    limitations: ["免責","商標利用禁止"],
    commercial: true, modify: true, distribute: true, patent: true, private: true,
    copyleft: true, attribution: true, networkUse: false,
    color: "#7c3aed",
    template: `Mozilla Public License Version 2.0

Copyright (c) {{YEAR}} {{NAME}}

This Source Code Form is subject to the terms of the Mozilla Public
License, v. 2.0. If a copy of the MPL was not distributed with this
file, You can obtain one at https://mozilla.org/MPL/2.0/.`
  },
  {
    id: "unlicense",
    name: "Unlicense",
    fullName: "The Unlicense",
    type: "public-domain",
    badge: "public",
    tldr: "パブリックドメイン宣言。著作権を完全に放棄。クレジット不要・条件なし。最大限の自由。",
    permissions: ["商用利用","改変","再配布","私的利用"],
    conditions: [],
    limitations: ["免責"],
    commercial: true, modify: true, distribute: true, patent: false, private: true,
    copyleft: false, attribution: false, networkUse: false,
    color: "#6b7280",
    template: `This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or
distribute this software, either in source code form or as a compiled
binary, for any purpose, commercial or non-commercial, and by any means.

In jurisdictions that recognize copyright laws, the author or authors
of this software dedicate any and all copyright interest in the software
to the public domain.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.

For more information, please refer to <https://unlicense.org>`
  },
  {
    id: "cc0",
    name: "CC0 1.0",
    fullName: "Creative Commons Zero v1.0 Universal",
    type: "public-domain",
    badge: "public",
    tldr: "Creative Commonsのパブリックドメイン宣言。データ・コンテンツ向けに推奨。ソフトウェアには特許付与がなくUnlicenseの方が適切な場合も。",
    permissions: ["商用利用","改変","再配布","私的利用"],
    conditions: [],
    limitations: ["免責","特許付与なし","商標利用禁止"],
    commercial: true, modify: true, distribute: true, patent: false, private: true,
    copyleft: false, attribution: false, networkUse: false,
    color: "#4b5563",
    template: `CC0 1.0 Universal

Statement of Purpose

To the extent possible under law, {{NAME}} has waived all copyright and
related or neighboring rights to this work. This work is published from
Japan, {{YEAR}}.

You should have received a copy of the CC0 legalcode along with this work.
If not, see <https://creativecommons.org/publicdomain/zero/1.0/>.`
  }
];

var QUESTIONS = [
  {
    id: "commercial",
    q: "商用利用を許可しますか？",
    hint: "企業が製品に組み込んだり販売したりすることを許可するか。",
    options: [
      { label: "はい、商用利用を許可する", value: true },
      { label: "いいえ、商用利用を制限したい", value: false }
    ]
  },
  {
    id: "patent",
    q: "特許権を明示的に付与しますか？",
    hint: "コントリビューターの特許をユーザーが侵害しないよう保護する条項。",
    options: [
      { label: "はい、特許付与を含める（推奨）", value: true },
      { label: "明示的な特許付与は不要", value: false }
    ]
  },
  {
    id: "copyleft",
    q: "コピーレフト（シェアアライク）を採用しますか？",
    hint: "派生物に同じライセンスを適用させるかどうか。",
    options: [
      { label: "不要 — 許容型にしたい", value: "none" },
      { label: "弱コピーレフト（ファイル・ライブラリ単位）", value: "weak" },
      { label: "強コピーレフト（すべての派生物）", value: "strong" }
    ]
  },
  {
    id: "attribution",
    q: "著作権表示（クレジット）の保持を要求しますか？",
    hint: "多くの許容型ライセンスでも著作権表示の保持は必要。",
    options: [
      { label: "はい、著作権表示を保持させる", value: true },
      { label: "一切の制限なし（パブリックドメイン）", value: false }
    ]
  }
];

var answers = {};
var currentStep = 0;

function olSwitchTab(tab) {
  document.querySelectorAll('#ol-app .ol-tab-btn').forEach(function(b) { b.classList.remove('active'); });
  document.querySelectorAll('#ol-app .ol-panel').forEach(function(p) { p.classList.remove('active'); });
  var btn = document.querySelector('#ol-app .ol-tab-btn[onclick*="' + tab + '"]');
  if (btn) btn.classList.add('active');
  var panel = document.getElementById('ol-panel-' + tab);
  if (panel) panel.classList.add('active');
}
window.olSwitchTab = olSwitchTab;

function renderWizard() {
  renderStepIndicator();
  var body = document.getElementById('ol-wizard-body');
  if (currentStep < QUESTIONS.length) {
    var q = QUESTIONS[currentStep];
    var html = '<div class="ol-wizard-step"><h3>' + q.q + '</h3><p>' + q.hint + '</p><div class="ol-btn-group">';
    q.options.forEach(function(opt) {
      var sel = answers[q.id] === opt.value ? ' selected' : '';
      html += '<button class="ol-choice-btn' + sel + '" onclick="olAnswer(\'' + q.id + '\',' + JSON.stringify(opt.value) + ')">' + opt.label + '</button>';
    });
    html += '</div></div>';
    if (currentStep > 0) {
      html += '<button class="ol-reset-btn" onclick="olBack()">← 戻る</button>';
    }
    body.innerHTML = html;
  } else {
    renderResult();
  }
}

function olAnswer(qid, val) {
  answers[qid] = val;
  currentStep++;
  renderWizard();
}
window.olAnswer = olAnswer;

function olBack() {
  if (currentStep > 0) {
    currentStep--;
    delete answers[QUESTIONS[currentStep].id];
    renderWizard();
  }
}
window.olBack = olBack;

function renderStepIndicator() {
  var ind = document.getElementById('ol-step-indicator');
  var html = '';
  QUESTIONS.forEach(function(q, i) {
    var cls = i < currentStep ? 'done' : i === currentStep ? 'current' : '';
    html += '<div class="ol-step-dot ' + cls + '">' + (i + 1) + '</div>';
    if (i < QUESTIONS.length - 1) {
      html += '<div class="ol-step-line ' + (i < currentStep ? 'done' : '') + '"></div>';
    }
  });
  ind.innerHTML = html;
}

function scoreLicense(lic) {
  var score = 0;
  if (answers.commercial === true && lic.commercial) score += 2;
  if (answers.commercial === false && !lic.commercial) score += 2;
  if (answers.patent === true && lic.patent) score += 3;
  if (answers.patent === false && !lic.patent) score += 1;
  if (answers.copyleft === 'none' && !lic.copyleft) score += 3;
  if (answers.copyleft === 'weak' && lic.type === 'weak-copyleft') score += 4;
  if (answers.copyleft === 'strong' && lic.type === 'copyleft') score += 4;
  if (answers.copyleft === 'strong' && lic.type === 'weak-copyleft') score += 2;
  if (answers.attribution === true && lic.attribution) score += 2;
  if (answers.attribution === false && !lic.attribution) score += 3;
  return score;
}

function renderResult() {
  var scored = LICENSES.map(function(l) { return { lic: l, score: scoreLicense(l) }; });
  scored.sort(function(a, b) { return b.score - a.score; });
  var best = scored[0].lic;
  var runner = scored[1].lic;

  var body = document.getElementById('ol-wizard-body');
  var html = '<div class="ol-result-box">';
  html += '<h3>おすすめ: ' + best.fullName + '</h3>';
  html += '<p class="ol-tldr">' + best.tldr + '</p>';
  html += shieldHtml(best);
  html += '<div class="ol-result-actions">';
  html += '<button class="ol-btn-primary" onclick="olOpenModal(\'' + best.id + '\')">ライセンス文を見る・コピー</button>';
  html += '<button class="ol-btn-secondary" onclick="olSwitchTab(\'compare\')">全ライセンス比較</button>';
  html += '</div></div>';

  html += '<div style="margin-top:16px;padding:16px;background:#f8fafc;border-radius:10px;border:1px solid #e2e8f0;">';
  html += '<strong style="font-size:13px;color:#64748b;">次点候補:</strong> ';
  html += '<span class="ol-license-name" style="color:#4f46e5;cursor:pointer;font-weight:700;" onclick="olOpenModal(\'' + runner.id + '\')">' + runner.fullName + '</span>';
  html += ' — <span style="font-size:13px;color:#64748b;">' + runner.tldr + '</span>';
  html += '</div>';

  html += '<button class="ol-reset-btn" onclick="olReset()">最初からやり直す</button>';
  body.innerHTML = html;
}

function olReset() { answers = {}; currentStep = 0; renderWizard(); }
window.olReset = olReset;

function chk(val) { return val ? '<span class="ol-check">✓</span>' : '<span class="ol-cross">✗</span>'; }

function badgeHtml(lic) {
  var labels = { permissive: '許容型', copyleft: '強コピーレフト', 'weak-copyleft': '弱コピーレフト', 'public-domain': 'パブリックドメイン' };
  return '<span class="ol-badge ol-badge-' + lic.badge + '">' + labels[lic.type] + '</span>';
}

function shieldHtml(lic) {
  var colors = { permissive: '#16a34a', copyleft: '#dc2626', 'weak-copyleft': '#d97706', 'public-domain': '#4f46e5' };
  var c = colors[lic.type] || '#555';
  return '<div class="ol-shields-row"><div class="ol-shield"><span class="ol-shield-left">license</span><span class="ol-shield-right" style="background:' + c + '">' + lic.name + '</span></div></div>';
}

function renderTable() {
  var tbody = document.getElementById('ol-compare-body');
  var html = '';
  LICENSES.forEach(function(lic) {
    html += '<tr>';
    html += '<td><span class="ol-license-name" onclick="olOpenModal(\'' + lic.id + '\')">' + lic.fullName + '</span><br>' + shieldHtml(lic) + '</td>';
    html += '<td>' + badgeHtml(lic) + '</td>';
    html += '<td>' + chk(lic.commercial) + '</td>';
    html += '<td>' + chk(lic.modify) + '</td>';
    html += '<td>' + chk(lic.distribute) + '</td>';
    html += '<td>' + chk(lic.patent) + '</td>';
    html += '<td>' + chk(lic.private) + '</td>';
    html += '<td>' + chk(lic.copyleft) + '</td>';
    html += '<td>' + chk(lic.attribution) + '</td>';
    html += '<td>' + chk(lic.networkUse) + '</td>';
    html += '</tr>';
  });
  tbody.innerHTML = html;
}

function olOpenModal(licId) {
  var lic = LICENSES.find(function(l) { return l.id === licId; });
  if (!lic) return;
  var content = document.getElementById('ol-modal-content');

  var perms = lic.permissions.map(function(p) { return '<span class="ol-pill ol-pill-green">' + p + '</span>'; }).join('');
  var conds = lic.conditions.length ? lic.conditions.map(function(c) { return '<span class="ol-pill ol-pill-blue">' + c + '</span>'; }).join('') : '<span style="color:#94a3b8;font-size:13px;">なし</span>';
  var lims = lic.limitations.map(function(l) { return '<span class="ol-pill ol-pill-red">' + l + '</span>'; }).join('');

  var html = '<h2>' + lic.fullName + '</h2>';
  html += '<p class="ol-modal-tldr">' + lic.tldr + '</p>';
  html += shieldHtml(lic);
  html += '<div class="ol-modal-section"><h4>できること</h4><div class="ol-pill-list">' + perms + '</div></div>';
  html += '<div class="ol-modal-section"><h4>条件</h4><div class="ol-pill-list">' + conds + '</div></div>';
  html += '<div class="ol-modal-section"><h4>制限</h4><div class="ol-pill-list">' + lims + '</div></div>';

  html += '<div class="ol-modal-section"><h4>ライセンス文のコピー</h4>';
  html += '<div class="ol-copy-row">';
  html += '<input class="ol-input-sm" id="ol-inp-year" type="text" placeholder="年（例: 2025）" value="' + new Date().getFullYear() + '">';
  html += '<input class="ol-input-sm" id="ol-inp-name" type="text" placeholder="名前 / 組織名">';
  html += '<button class="ol-copy-btn" id="ol-copy-btn" onclick="olCopyText(\'' + licId + '\')">コピー</button>';
  html += '</div>';
  html += '<pre id="ol-license-pre">' + escHtml(lic.template) + '</pre>';
  html += '</div>';

  content.innerHTML = html;
  document.getElementById('ol-modal').classList.add('open');

  ['ol-inp-year', 'ol-inp-name'].forEach(function(id) {
    document.getElementById(id).addEventListener('input', function() { updatePreview(licId); });
  });
}
window.olOpenModal = olOpenModal;

function updatePreview(licId) {
  var lic = LICENSES.find(function(l) { return l.id === licId; });
  if (!lic) return;
  var year = document.getElementById('ol-inp-year').value || '{{YEAR}}';
  var name = document.getElementById('ol-inp-name').value || '{{NAME}}';
  var text = lic.template.replace(/\{\{YEAR\}\}/g, year).replace(/\{\{NAME\}\}/g, name);
  document.getElementById('ol-license-pre').textContent = text;
}

function olCopyText(licId) {
  var text = document.getElementById('ol-license-pre').textContent;
  if (navigator.clipboard) {
    navigator.clipboard.writeText(text).then(flashCopy);
  } else {
    var ta = document.createElement('textarea');
    ta.value = text; document.body.appendChild(ta); ta.select();
    document.execCommand('copy'); document.body.removeChild(ta);
    flashCopy();
  }
}
window.olCopyText = olCopyText;

function flashCopy() {
  var btn = document.getElementById('ol-copy-btn');
  btn.textContent = 'コピー完了！'; btn.classList.add('copied');
  setTimeout(function() { btn.textContent = 'コピー'; btn.classList.remove('copied'); }, 2000);
}

function olCloseModal(e, force) {
  if (force || (e && e.target === document.getElementById('ol-modal'))) {
    document.getElementById('ol-modal').classList.remove('open');
  }
}
window.olCloseModal = olCloseModal;

function escHtml(s) {
  return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

renderWizard();
renderTable();

})();
</script>

</div>

---

## ライセンス選択の基礎知識

**許容型（Permissive）** — MIT・Apache 2.0・BSD系は制約が少なく、商用プロダクトへの組み込みも自由。採用実績が多く、広く使われることを優先したい場合の第一選択。Apache 2.0は特許付与を明示するため、企業プロジェクトに適する。

**強コピーレフト** — GPL v2/v3は派生物を同じライセンスで公開させる義務が生じる。OSSへの改善の還元を重視するプロジェクトや、プロプライエタリな独占利用を防ぎたい場合に選択。

**弱コピーレフト** — LGPL・MPL 2.0はライブラリや変更ファイル単位でコピーレフトを適用。プロプライエタリなソフトウェアからリンクして利用することを許容しつつ、ライブラリ本体の改善は還元させたい場合に適する。

**パブリックドメイン** — UnlicenseやCC0は著作権を完全に放棄。条件なし・クレジット不要。ソフトウェア向けにはUnlicenseが、データ・コンテンツ向けにはCC0が推奨される。

### 目的別クイックガイド

| 目的 | 推奨ライセンス |
|---|---|
| 最大限の採用を促したい | MIT |
| 特許保護も含めたい | Apache 2.0 |
| 派生物を必ずオープンにしたい | GPL v3 |
| ライブラリ、プロプライエタリなリンクも許可 | LGPL または MPL 2.0 |
| 制限を一切設けたい | Unlicense |

**関連ツール:** [Gitコマンドジェネレーター](/ja/tools/git-command-generator/) &mdash; [変更履歴ジェネレーター](/ja/tools/changelog-generator/)

---

## freeeで経理・請求書管理を効率化

<div style="background:linear-gradient(135deg,#1a56db 0%,#1e40af 100%);border-radius:14px;padding:28px 32px;margin:32px 0;color:#fff;">
  <div style="font-size:13px;font-weight:600;opacity:0.8;margin-bottom:6px;letter-spacing:0.05em;">PR / 広告</div>
  <h3 style="margin:0 0 10px;font-size:20px;font-weight:800;">freee会計 — 個人事業主・スタートアップの定番クラウド会計</h3>
  <p style="margin:0 0 18px;font-size:14px;opacity:0.9;line-height:1.6;">確定申告・請求書・経費精算をまとめて自動化。OSSプロジェクトの副業収入や受託開発の請求管理にも最適。30日間無料トライアル実施中。</p>
  <a href="https://www.freee.co.jp/" target="_blank" rel="noopener sponsored" style="display:inline-block;background:#fff;color:#1a56db;font-weight:700;font-size:14px;padding:11px 26px;border-radius:8px;text-decoration:none;">freeeを無料で試す →</a>
</div>

---

<div style="font-size:11px;color:#94a3b8;margin-top:32px;padding-top:16px;border-top:1px solid #e2e8f0;line-height:1.6;">
本ページにはアフィリエイト広告が含まれています。<br>
<a href="https://www.a8.net/" target="_blank" rel="noopener" style="color:#94a3b8;">A8.net</a> を通じた成果報酬型広告を利用しています。掲載内容は編集部が独自に選定しており、広告主からの依頼による誘導は行っていません。
</div>
