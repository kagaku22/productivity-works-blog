---
title: "Open Source License Chooser"
slug: "license-chooser"
date: 2025-05-16
description: "Free open source license chooser. Compare MIT, Apache 2.0, GPL, BSD, and other licenses side by side. Answer questions to find the right license for your project."
categories: ["Free Tools"]
tags: ["open source", "license", "MIT", "Apache", "GPL", "BSD", "developer tools"]
ShowToc: false
cover:
  image: "/images/covers/license-chooser.png"
  alt: "Open Source License Chooser"
---

A free tool to help you choose the right open source license. Answer a few questions to get a recommendation, compare licenses side by side, and copy ready-to-use license text.

**Related tools:** [Git Command Generator](/tools/git-command-generator/) &mdash; [Changelog Generator](/tools/changelog-generator/)

<div id="ol-app">

<style>
#ol-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
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
  font-weight: 600;
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
#ol-app .ol-wizard-step h3 {
  margin: 0 0 8px;
  font-size: 17px;
  color: #1e293b;
}
#ol-app .ol-wizard-step p {
  margin: 0 0 16px;
  color: #64748b;
  font-size: 14px;
}
#ol-app .ol-btn-group {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}
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
#ol-app .ol-step-indicator {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 24px;
}
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
#ol-app .ol-step-line {
  flex: 1; height: 2px; background: #e2e8f0;
}
#ol-app .ol-step-line.done { background: #4f46e5; }

#ol-app .ol-result-box {
  border: 2px solid #4f46e5;
  border-radius: 12px;
  padding: 28px;
  background: #eef2ff;
  margin-top: 24px;
}
#ol-app .ol-result-box h3 { margin: 0 0 6px; color: #4f46e5; font-size: 20px; }
#ol-app .ol-result-box .ol-tldr {
  font-size: 14px; color: #334155; margin-bottom: 16px;
}
#ol-app .ol-result-actions { display: flex; gap: 10px; flex-wrap: wrap; margin-top: 16px; }
#ol-app .ol-btn-primary {
  padding: 10px 20px;
  background: #4f46e5; color: #fff;
  border: none; border-radius: 8px;
  cursor: pointer; font-size: 14px; font-weight: 600;
  transition: background 0.2s;
}
#ol-app .ol-btn-primary:hover { background: #4338ca; }
#ol-app .ol-btn-secondary {
  padding: 10px 20px;
  background: #fff; color: #4f46e5;
  border: 2px solid #4f46e5; border-radius: 8px;
  cursor: pointer; font-size: 14px; font-weight: 600;
  transition: all 0.2s;
}
#ol-app .ol-btn-secondary:hover { background: #eef2ff; }

/* Comparison table */
#ol-app .ol-table-wrap { overflow-x: auto; }
#ol-app .ol-table {
  width: 100%; border-collapse: collapse;
  font-size: 13px;
}
#ol-app .ol-table th {
  background: #1e293b; color: #fff;
  padding: 10px 14px; text-align: left;
  white-space: nowrap;
  position: sticky; top: 0;
}
#ol-app .ol-table td {
  padding: 9px 14px;
  border-bottom: 1px solid #e2e8f0;
  vertical-align: top;
}
#ol-app .ol-table tr:hover td { background: #f8fafc; }
#ol-app .ol-table .ol-license-name {
  font-weight: 700; color: #4f46e5; cursor: pointer;
  white-space: nowrap;
}
#ol-app .ol-table .ol-license-name:hover { text-decoration: underline; }
#ol-app .ol-check { color: #16a34a; font-weight: 700; }
#ol-app .ol-cross { color: #dc2626; font-weight: 700; }
#ol-app .ol-partial { color: #d97706; font-weight: 700; }

/* Badge */
#ol-app .ol-badge {
  display: inline-block;
  padding: 2px 10px;
  border-radius: 4px;
  font-size: 11px; font-weight: 700;
  letter-spacing: 0.02em;
}
#ol-app .ol-badge-permissive { background: #dcfce7; color: #15803d; }
#ol-app .ol-badge-copyleft  { background: #fee2e2; color: #b91c1c; }
#ol-app .ol-badge-weak     { background: #fef3c7; color: #92400e; }
#ol-app .ol-badge-public   { background: #e0e7ff; color: #3730a3; }

/* Detail modal */
#ol-app .ol-modal-backdrop {
  display: none;
  position: fixed; inset: 0;
  background: rgba(0,0,0,0.5);
  z-index: 1000;
  align-items: center; justify-content: center;
}
#ol-app .ol-modal-backdrop.open { display: flex; }
#ol-app .ol-modal {
  background: #fff;
  border-radius: 14px;
  max-width: 680px; width: 95vw;
  max-height: 85vh;
  overflow-y: auto;
  padding: 32px;
  position: relative;
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
#ol-app .ol-modal h2 { margin: 0 0 4px; font-size: 22px; color: #1e293b; }
#ol-app .ol-modal .ol-modal-tldr {
  color: #64748b; font-size: 14px; margin-bottom: 20px;
}
#ol-app .ol-modal pre {
  background: #0f172a; color: #e2e8f0;
  padding: 20px; border-radius: 10px;
  font-size: 12px; line-height: 1.6;
  white-space: pre-wrap; word-break: break-word;
  max-height: 300px; overflow-y: auto;
}
#ol-app .ol-copy-row {
  display: flex; gap: 8px; margin-bottom: 14px; flex-wrap: wrap;
}
#ol-app .ol-input-sm {
  padding: 7px 10px;
  border: 1px solid #cbd5e1;
  border-radius: 6px; font-size: 13px;
  width: 160px;
}
#ol-app .ol-copy-btn {
  padding: 7px 16px;
  background: #4f46e5; color: #fff;
  border: none; border-radius: 6px;
  cursor: pointer; font-size: 13px; font-weight: 600;
  transition: background 0.2s;
}
#ol-app .ol-copy-btn:hover { background: #4338ca; }
#ol-app .ol-copy-btn.copied { background: #16a34a; }
#ol-app .ol-shields-row { display: flex; align-items: center; gap: 10px; flex-wrap: wrap; margin-top: 12px; }
#ol-app .ol-shield {
  display: inline-flex; align-items: center;
  border-radius: 4px; overflow: hidden;
  font-size: 11px; font-weight: 600; height: 20px;
}
#ol-app .ol-shield-left { background: #555; color: #fff; padding: 0 6px; }
#ol-app .ol-shield-right { padding: 0 8px; color: #fff; }

/* Sections in modal */
#ol-app .ol-modal-section { margin-bottom: 18px; }
#ol-app .ol-modal-section h4 { font-size: 13px; text-transform: uppercase; letter-spacing: 0.06em; color: #94a3b8; margin: 0 0 8px; }
#ol-app .ol-pill-list { display: flex; flex-wrap: wrap; gap: 6px; }
#ol-app .ol-pill {
  padding: 3px 10px; border-radius: 20px; font-size: 12px; font-weight: 500;
}
#ol-app .ol-pill-green { background: #dcfce7; color: #15803d; }
#ol-app .ol-pill-red   { background: #fee2e2; color: #b91c1c; }
#ol-app .ol-pill-blue  { background: #dbeafe; color: #1d4ed8; }

/* Reset btn */
#ol-app .ol-reset-btn {
  padding: 8px 16px; border: 1px solid #e2e8f0;
  border-radius: 8px; background: #fff; cursor: pointer;
  font-size: 13px; color: #64748b; margin-top: 12px;
}
#ol-app .ol-reset-btn:hover { border-color: #94a3b8; color: #334155; }
</style>

<div class="ol-tabs">
  <button class="ol-tab-btn active" onclick="olSwitchTab('wizard')">Wizard</button>
  <button class="ol-tab-btn" onclick="olSwitchTab('compare')">Compare All</button>
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
          <th>License</th>
          <th>Type</th>
          <th>Commercial Use</th>
          <th>Modify</th>
          <th>Distribute</th>
          <th>Patent Grant</th>
          <th>Private Use</th>
          <th>Copyleft</th>
          <th>Attribution</th>
          <th>Network Use</th>
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

// ─── License data ───────────────────────────────────────────────────────────
var LICENSES = [
  {
    id: "mit",
    name: "MIT",
    fullName: "MIT License",
    type: "permissive",
    badge: "permissive",
    tldr: "Short and simple permissive license. Lets people do almost anything with your code as long as they include the original copyright and license notice.",
    permissions: ["Commercial use","Modification","Distribution","Private use"],
    conditions: ["License and copyright notice"],
    limitations: ["Liability","Warranty"],
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
    tldr: "Permissive license with an explicit grant of patent rights from contributors to users. Requires preservation of copyright and license notices.",
    permissions: ["Commercial use","Modification","Distribution","Patent use","Private use"],
    conditions: ["License and copyright notice","State changes","Notice file if present"],
    limitations: ["Liability","Trademark use","Warranty"],
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
    tldr: "Strong copyleft license. Derivative works must be open-sourced under the same license. Includes patent protection and anti-tivoization provisions.",
    permissions: ["Commercial use","Modification","Distribution","Patent use","Private use"],
    conditions: ["Disclose source","License and copyright notice","Same license","State changes"],
    limitations: ["Liability","Warranty"],
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
    tldr: "Classic strong copyleft license. Derivative works must be distributed under the same license. No explicit patent grant.",
    permissions: ["Commercial use","Modification","Distribution","Private use"],
    conditions: ["Disclose source","License and copyright notice","Same license","State changes"],
    limitations: ["Liability","Warranty"],
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
    tldr: "Weak copyleft license primarily for libraries. Allows linking from proprietary software, but modifications to the library itself must be open-sourced.",
    permissions: ["Commercial use","Modification","Distribution","Private use"],
    conditions: ["Disclose source","License and copyright notice","Same license (library changes only)","State changes"],
    limitations: ["Liability","Warranty"],
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
    tldr: "Permissive license with two simple conditions: preserve the copyright notice in source and binary distributions.",
    permissions: ["Commercial use","Modification","Distribution","Private use"],
    conditions: ["License and copyright notice"],
    limitations: ["Liability","Warranty"],
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
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.`
  },
  {
    id: "bsd3",
    name: "BSD 3-Clause",
    fullName: 'BSD 3-Clause "New" or "Revised" License',
    type: "permissive",
    badge: "permissive",
    tldr: "Like BSD 2-Clause plus a non-endorsement clause: you cannot use the project name or contributors to promote derivative products without permission.",
    permissions: ["Commercial use","Modification","Distribution","Private use"],
    conditions: ["License and copyright notice","No endorsement"],
    limitations: ["Liability","Warranty"],
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
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.`
  },
  {
    id: "mpl2",
    name: "MPL 2.0",
    fullName: "Mozilla Public License 2.0",
    type: "weak-copyleft",
    badge: "weak",
    tldr: "File-level copyleft: modifications to existing files must be open-sourced, but you can combine MPL code with proprietary code in separate files.",
    permissions: ["Commercial use","Modification","Distribution","Patent use","Private use"],
    conditions: ["Disclose source (modified files only)","License and copyright notice","Same license (modified files only)"],
    limitations: ["Liability","Trademark use","Warranty"],
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
    tldr: "Dedication to the public domain. No restrictions whatsoever — anyone can do anything with the code, no credit required.",
    permissions: ["Commercial use","Modification","Distribution","Private use"],
    conditions: [],
    limitations: ["Liability","Warranty"],
    commercial: true, modify: true, distribute: true, patent: false, private: true,
    copyleft: false, attribution: false, networkUse: false,
    color: "#6b7280",
    template: `This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or
distribute this software, either in source code form or as a compiled
binary, for any purpose, commercial or non-commercial, and by any means.

In jurisdictions that recognize copyright laws, the author or authors
of this software dedicate any and all copyright interest in the software
to the public domain. We make this dedication for the benefit of the
public at large and to the detriment of our heirs and successors. We
intend this dedication to be an overt act of relinquishment in perpetuity
of all present and future rights to this software under copyright law.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR
OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

For more information, please refer to <https://unlicense.org>`
  },
  {
    id: "cc0",
    name: "CC0 1.0",
    fullName: "Creative Commons Zero v1.0 Universal",
    type: "public-domain",
    badge: "public",
    tldr: "Creative Commons public domain dedication. Waives all copyright to the fullest extent possible under law. Often used for data and creative works, not recommended for software.",
    permissions: ["Commercial use","Modification","Distribution","Private use"],
    conditions: [],
    limitations: ["Liability","Patent use","Trademark use","Warranty"],
    commercial: true, modify: true, distribute: true, patent: false, private: true,
    copyleft: false, attribution: false, networkUse: false,
    color: "#4b5563",
    template: `CC0 1.0 Universal

Statement of Purpose

The laws of most jurisdictions throughout the world automatically confer
exclusive Copyright and Related Rights (defined below) upon the creator and
subsequent owner(s) of an original work of authorship and/or a database.

To the extent possible under law, {{NAME}} has waived all copyright and
related or neighboring rights to this work. This work is published from the
United States, {{YEAR}}.

You should have received a copy of the CC0 legalcode along with this work.
If not, see <https://creativecommons.org/publicdomain/zero/1.0/>.`
  }
];

// Wizard questions
var QUESTIONS = [
  {
    id: "commercial",
    q: "Do you want to allow commercial use of your code?",
    hint: "Can companies use or sell products built with your code?",
    options: [
      { label: "Yes, anyone can use it commercially", value: true },
      { label: "No, restrict commercial use", value: false }
    ]
  },
  {
    id: "patent",
    q: "Do you want to explicitly grant patent rights?",
    hint: "Protects users from patent claims by contributors.",
    options: [
      { label: "Yes, include patent grant (recommended)", value: true },
      { label: "No explicit patent grant needed", value: false }
    ]
  },
  {
    id: "copyleft",
    q: "Do you want copyleft (share-alike)?",
    hint: "Requires derivative works to use the same license.",
    options: [
      { label: "No — keep it permissive", value: "none" },
      { label: "Weak copyleft (file/library level)", value: "weak" },
      { label: "Strong copyleft (all derivatives)", value: "strong" }
    ]
  },
  {
    id: "attribution",
    q: "Must users credit you / include your license notice?",
    hint: "Even permissive licenses often require keeping your copyright notice.",
    options: [
      { label: "Yes, require attribution", value: true },
      { label: "No restrictions at all (public domain)", value: false }
    ]
  }
];

// State
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

// ─── Wizard ──────────────────────────────────────────────────────────────────
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
      html += '<button class="ol-reset-btn" onclick="olBack()">← Back</button>';
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
    var qid = QUESTIONS[currentStep].id;
    delete answers[qid];
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
  // commercial
  if (answers.commercial === true && lic.commercial) score += 2;
  if (answers.commercial === false && !lic.commercial) score += 2;
  // patent
  if (answers.patent === true && lic.patent) score += 3;
  if (answers.patent === false && !lic.patent) score += 1;
  // copyleft
  if (answers.copyleft === 'none' && !lic.copyleft) score += 3;
  if (answers.copyleft === 'weak' && lic.type === 'weak-copyleft') score += 4;
  if (answers.copyleft === 'strong' && lic.type === 'copyleft') score += 4;
  if (answers.copyleft === 'strong' && lic.type === 'weak-copyleft') score += 2;
  // attribution
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
  html += '<h3>Recommended: ' + best.fullName + '</h3>';
  html += '<p class="ol-tldr">' + best.tldr + '</p>';
  html += shieldHtml(best);
  html += '<div class="ol-result-actions">';
  html += '<button class="ol-btn-primary" onclick="olOpenModal(\'' + best.id + '\')">View License Text &amp; Copy</button>';
  html += '<button class="ol-btn-secondary" onclick="olSwitchTab(\'compare\')">Compare All Licenses</button>';
  html += '</div></div>';

  html += '<div style="margin-top:16px;padding:16px;background:#f8fafc;border-radius:10px;border:1px solid #e2e8f0;">';
  html += '<strong style="font-size:13px;color:#64748b;">Runner-up:</strong> ';
  html += '<span class="ol-license-name" style="color:#4f46e5;cursor:pointer;font-weight:700;" onclick="olOpenModal(\'' + runner.id + '\')">' + runner.fullName + '</span>';
  html += ' — <span style="font-size:13px;color:#64748b;">' + runner.tldr + '</span>';
  html += '</div>';

  html += '<button class="ol-reset-btn" onclick="olReset()">Start Over</button>';
  body.innerHTML = html;
}

function olReset() {
  answers = {};
  currentStep = 0;
  renderWizard();
}
window.olReset = olReset;

// ─── Comparison table ────────────────────────────────────────────────────────
function chk(val) { return val ? '<span class="ol-check">✓</span>' : '<span class="ol-cross">✗</span>'; }

function badgeHtml(lic) {
  var labels = { permissive: 'Permissive', copyleft: 'Copyleft', 'weak-copyleft': 'Weak Copyleft', 'public-domain': 'Public Domain' };
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

// ─── Modal ───────────────────────────────────────────────────────────────────
function olOpenModal(licId) {
  var lic = LICENSES.find(function(l) { return l.id === licId; });
  if (!lic) return;
  var content = document.getElementById('ol-modal-content');

  var perms = lic.permissions.map(function(p) { return '<span class="ol-pill ol-pill-green">' + p + '</span>'; }).join('');
  var conds = lic.conditions.length ? lic.conditions.map(function(c) { return '<span class="ol-pill ol-pill-blue">' + c + '</span>'; }).join('') : '<span style="color:#94a3b8;font-size:13px;">None</span>';
  var lims = lic.limitations.map(function(l) { return '<span class="ol-pill ol-pill-red">' + l + '</span>'; }).join('');

  var html = '<h2>' + lic.fullName + '</h2>';
  html += '<p class="ol-modal-tldr">' + lic.tldr + '</p>';
  html += shieldHtml(lic);
  html += '<div class="ol-modal-section"><h4>Permissions</h4><div class="ol-pill-list">' + perms + '</div></div>';
  html += '<div class="ol-modal-section"><h4>Conditions</h4><div class="ol-pill-list">' + conds + '</div></div>';
  html += '<div class="ol-modal-section"><h4>Limitations</h4><div class="ol-pill-list">' + lims + '</div></div>';

  html += '<div class="ol-modal-section"><h4>Copy License Text</h4>';
  html += '<div class="ol-copy-row">';
  html += '<input class="ol-input-sm" id="ol-inp-year" type="text" placeholder="Year (e.g. 2025)" value="' + new Date().getFullYear() + '">';
  html += '<input class="ol-input-sm" id="ol-inp-name" type="text" placeholder="Your name / org">';
  html += '<button class="ol-copy-btn" id="ol-copy-btn" onclick="olCopyText(\'' + licId + '\')">Copy</button>';
  html += '</div>';
  html += '<pre id="ol-license-pre">' + escHtml(lic.template) + '</pre>';
  html += '</div>';

  content.innerHTML = html;
  document.getElementById('ol-modal').classList.add('open');

  // Live preview update
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
    navigator.clipboard.writeText(text).then(function() { flashCopy(); });
  } else {
    var ta = document.createElement('textarea');
    ta.value = text;
    document.body.appendChild(ta);
    ta.select();
    document.execCommand('copy');
    document.body.removeChild(ta);
    flashCopy();
  }
}
window.olCopyText = olCopyText;

function flashCopy() {
  var btn = document.getElementById('ol-copy-btn');
  btn.textContent = 'Copied!';
  btn.classList.add('copied');
  setTimeout(function() { btn.textContent = 'Copy'; btn.classList.remove('copied'); }, 2000);
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

// ─── Init ────────────────────────────────────────────────────────────────────
renderWizard();
renderTable();

})();
</script>

</div>

---

## How to Choose a License

**Permissive licenses** (MIT, Apache 2.0, BSD) let anyone use your code with minimal restrictions. MIT is the most popular for open-source projects. Apache 2.0 adds an explicit patent grant, making it better suited for larger projects.

**Copyleft licenses** (GPL v2/v3) require derivative works to be released under the same license. Use these when you want improvements to always remain open.

**Weak copyleft** (LGPL, MPL 2.0) applies copyleft only at the file or library boundary, letting proprietary software link against your library.

**Public domain** (Unlicense, CC0) waives all copyright. Maximum freedom for users, but note that CC0 is recommended for data/content, not software.

### Quick Reference

| Goal | Recommended |
|---|---|
| Maximum adoption | MIT |
| Patent protection | Apache 2.0 |
| Keep derivatives open | GPL v3 |
| Library, allow proprietary linking | LGPL or MPL 2.0 |
| No restrictions at all | Unlicense |

**Related tools:** [Git Command Generator](/tools/git-command-generator/) &mdash; [Changelog Generator](/tools/changelog-generator/)
