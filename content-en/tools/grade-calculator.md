---
title: "Grade Calculator - Weighted Average & Final Grade"
description: "Calculate your GPA, weighted grades, and final exam scores needed. Free online grade and GPA calculator."
date: 2025-05-16
categories: ["Free Tools"]
slug: "grade-calculator"
ShowToc: false
cover:
  image: "/images/covers/grade-calculator.png"
---

<div id="gc-app">
<style>
#gc-app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  max-width: 860px;
  margin: 0 auto;
  padding: 16px;
  color: #1a1a2e;
  box-sizing: border-box;
}
#gc-app *, #gc-app *::before, #gc-app *::after { box-sizing: inherit; }
#gc-app h2 {
  font-size: 1.4rem;
  font-weight: 700;
  margin: 0 0 4px;
  color: #1a1a2e;
}
#gc-app .gc-subtitle {
  font-size: 0.9rem;
  color: #666;
  margin: 0 0 20px;
}
#gc-app .gc-card {
  background: #fff;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 16px;
  box-shadow: 0 1px 4px rgba(0,0,0,0.05);
}
#gc-app .gc-card-title {
  font-size: 1rem;
  font-weight: 600;
  margin: 0 0 14px;
  display: flex;
  align-items: center;
  gap: 8px;
}
#gc-app .gc-card-title span.icon {
  font-size: 1.1rem;
}
#gc-app table.gc-table {
  width: 100%;
  border-collapse: collapse;
}
#gc-app table.gc-table th {
  text-align: left;
  font-size: 0.75rem;
  font-weight: 600;
  color: #888;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  padding: 0 6px 8px;
  border-bottom: 2px solid #f0f0f0;
}
#gc-app table.gc-table td {
  padding: 6px 6px;
  vertical-align: middle;
}
#gc-app table.gc-table td input {
  width: 100%;
  padding: 7px 9px;
  border: 1px solid #dde1e7;
  border-radius: 7px;
  font-size: 0.9rem;
  color: #1a1a2e;
  background: #fafbfc;
  transition: border-color 0.15s;
  outline: none;
}
#gc-app table.gc-table td input:focus {
  border-color: #6366f1;
  background: #fff;
}
#gc-app table.gc-table td.gc-pct {
  font-size: 0.85rem;
  color: #6366f1;
  font-weight: 600;
  text-align: right;
  white-space: nowrap;
  padding-right: 4px;
}
#gc-app table.gc-table td.gc-grade-cell {
  text-align: center;
  font-size: 0.9rem;
  font-weight: 700;
}
#gc-app .gc-btn-remove {
  background: none;
  border: none;
  cursor: pointer;
  color: #cbd5e1;
  font-size: 1.1rem;
  padding: 4px 6px;
  border-radius: 5px;
  line-height: 1;
  transition: color 0.15s, background 0.15s;
}
#gc-app .gc-btn-remove:hover { color: #ef4444; background: #fef2f2; }
#gc-app .gc-add-row {
  margin-top: 12px;
  display: flex;
  align-items: center;
  gap: 10px;
  flex-wrap: wrap;
}
#gc-app .gc-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 8px 16px;
  border-radius: 8px;
  font-size: 0.875rem;
  font-weight: 600;
  cursor: pointer;
  border: none;
  transition: background 0.15s, transform 0.1s;
}
#gc-app .gc-btn:active { transform: scale(0.97); }
#gc-app .gc-btn-primary {
  background: #6366f1;
  color: #fff;
}
#gc-app .gc-btn-primary:hover { background: #4f46e5; }
#gc-app .gc-btn-secondary {
  background: #f1f5f9;
  color: #475569;
  border: 1px solid #e2e8f0;
}
#gc-app .gc-btn-secondary:hover { background: #e2e8f0; }
#gc-app .gc-weight-bar-wrap {
  margin-top: 10px;
  display: flex;
  align-items: center;
  gap: 10px;
}
#gc-app .gc-weight-bar-bg {
  flex: 1;
  height: 8px;
  background: #f0f0f0;
  border-radius: 99px;
  overflow: hidden;
}
#gc-app .gc-weight-bar-fill {
  height: 100%;
  border-radius: 99px;
  transition: width 0.3s, background 0.3s;
}
#gc-app .gc-weight-label {
  font-size: 0.82rem;
  font-weight: 600;
  min-width: 80px;
  text-align: right;
}
#gc-app .gc-summary-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: 12px;
  margin-bottom: 0;
}
#gc-app .gc-stat {
  background: #f8faff;
  border: 1px solid #e8edf5;
  border-radius: 10px;
  padding: 14px 16px;
  text-align: center;
}
#gc-app .gc-stat-label {
  font-size: 0.72rem;
  font-weight: 600;
  color: #888;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 6px;
}
#gc-app .gc-stat-value {
  font-size: 1.7rem;
  font-weight: 800;
  line-height: 1.1;
}
#gc-app .gc-stat-sub {
  font-size: 0.78rem;
  color: #888;
  margin-top: 3px;
}
#gc-app .gc-grade-badge {
  display: inline-block;
  padding: 2px 9px;
  border-radius: 99px;
  font-size: 0.8rem;
  font-weight: 700;
}
#gc-app .grade-Aplus  { color: #16a34a; background: #dcfce7; }
#gc-app .grade-A      { color: #16a34a; background: #dcfce7; }
#gc-app .grade-Aminus { color: #16a34a; background: #dcfce7; }
#gc-app .grade-Bplus  { color: #2563eb; background: #dbeafe; }
#gc-app .grade-B      { color: #2563eb; background: #dbeafe; }
#gc-app .grade-Bminus { color: #2563eb; background: #dbeafe; }
#gc-app .grade-Cplus  { color: #d97706; background: #fef3c7; }
#gc-app .grade-C      { color: #d97706; background: #fef3c7; }
#gc-app .grade-Cminus { color: #d97706; background: #fef3c7; }
#gc-app .grade-Dplus  { color: #ea580c; background: #ffedd5; }
#gc-app .grade-D      { color: #ea580c; background: #ffedd5; }
#gc-app .grade-F      { color: #dc2626; background: #fee2e2; }
#gc-app .grade-NA     { color: #94a3b8; background: #f1f5f9; }
#gc-app .gc-final-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 12px;
}
#gc-app .gc-final-input-row {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-top: 10px;
  flex-wrap: wrap;
}
#gc-app .gc-final-input-row label {
  font-size: 0.875rem;
  color: #475569;
  white-space: nowrap;
}
#gc-app .gc-final-input-row input, #gc-app .gc-final-input-row select {
  padding: 7px 10px;
  border: 1px solid #dde1e7;
  border-radius: 7px;
  font-size: 0.9rem;
  width: 90px;
  background: #fafbfc;
  outline: none;
  color: #1a1a2e;
}
#gc-app .gc-final-input-row input:focus, #gc-app .gc-final-input-row select:focus {
  border-color: #6366f1;
  background: #fff;
}
#gc-app .gc-final-result {
  margin-top: 14px;
  padding: 14px 16px;
  background: #f0f4ff;
  border-radius: 10px;
  border-left: 4px solid #6366f1;
  font-size: 0.95rem;
  color: #1a1a2e;
  line-height: 1.5;
}
#gc-app .gc-final-result strong { color: #4f46e5; }
#gc-app .gc-alert {
  padding: 10px 14px;
  border-radius: 8px;
  font-size: 0.85rem;
  margin-top: 10px;
}
#gc-app .gc-alert-warn { background: #fef3c7; color: #92400e; border: 1px solid #fde68a; }
#gc-app .gc-alert-ok   { background: #dcfce7; color: #166534; border: 1px solid #bbf7d0; }
#gc-app .gc-alert-err  { background: #fee2e2; color: #991b1b; border: 1px solid #fecaca; }
#gc-app .gc-gpa-row {
  display: flex;
  align-items: center;
  gap: 6px;
  margin-top: 8px;
  flex-wrap: wrap;
}
#gc-app .gc-gpa-scale {
  display: flex;
  gap: 4px;
  flex-wrap: wrap;
  margin-top: 10px;
}
#gc-app .gc-gpa-chip {
  font-size: 0.72rem;
  padding: 3px 8px;
  border-radius: 99px;
  background: #f1f5f9;
  color: #475569;
  border: 1px solid #e2e8f0;
}
#gc-app .gc-gpa-chip.active {
  background: #6366f1;
  color: #fff;
  border-color: #6366f1;
}
#gc-app .gc-related {
  margin-top: 6px;
  padding: 14px 18px;
  background: #f8faff;
  border-radius: 10px;
  border: 1px solid #e2e8f0;
}
#gc-app .gc-related h3 { font-size: 0.9rem; font-weight: 700; margin: 0 0 8px; color: #475569; }
#gc-app .gc-related ul { margin: 0; padding-left: 18px; }
#gc-app .gc-related li { font-size: 0.875rem; margin-bottom: 4px; }
#gc-app .gc-related a { color: #6366f1; text-decoration: none; }
#gc-app .gc-related a:hover { text-decoration: underline; }
#gc-app .gc-empty-row td {
  text-align: center;
  color: #aaa;
  font-size: 0.85rem;
  padding: 20px;
}
@media (max-width: 600px) {
  #gc-app table.gc-table th:nth-child(5),
  #gc-app table.gc-table td:nth-child(5) { display: none; }
}
</style>

<h2>Grade Calculator</h2>
<p class="gc-subtitle">Calculate weighted averages, letter grades, GPA, and find out what you need on your final exam.</p>

<!-- Assignments Card -->
<div class="gc-card">
  <div class="gc-card-title"><span class="icon">📋</span> Assignments &amp; Grades</div>
  <table class="gc-table" id="gc-table">
    <thead>
      <tr>
        <th style="width:30%">Assignment Name</th>
        <th style="width:15%">Score</th>
        <th style="width:15%">Max Score</th>
        <th style="width:15%">Weight (%)</th>
        <th style="width:12%">Grade</th>
        <th style="width:10%">%</th>
        <th style="width:3%"></th>
      </tr>
    </thead>
    <tbody id="gc-tbody">
    </tbody>
  </table>
  <div class="gc-add-row">
    <button class="gc-btn gc-btn-primary" onclick="gcAddRow()">+ Add Assignment</button>
    <button class="gc-btn gc-btn-secondary" onclick="gcReset()">Reset All</button>
  </div>
  <div class="gc-weight-bar-wrap">
    <div class="gc-weight-bar-bg">
      <div class="gc-weight-bar-fill" id="gc-weight-fill" style="width:0%;background:#6366f1;"></div>
    </div>
    <div class="gc-weight-label" id="gc-weight-label" style="color:#6366f1;">Total: 0%</div>
  </div>
  <div id="gc-weight-alert"></div>
</div>

<!-- Summary Card -->
<div class="gc-card">
  <div class="gc-card-title"><span class="icon">📊</span> Current Grade Summary</div>
  <div class="gc-summary-grid">
    <div class="gc-stat">
      <div class="gc-stat-label">Weighted Average</div>
      <div class="gc-stat-value" id="gc-wavg" style="color:#6366f1;">—</div>
      <div class="gc-stat-sub">out of 100%</div>
    </div>
    <div class="gc-stat">
      <div class="gc-stat-label">Letter Grade</div>
      <div class="gc-stat-value" id="gc-letter" style="font-size:2rem;">—</div>
      <div class="gc-stat-sub" id="gc-letter-sub"></div>
    </div>
    <div class="gc-stat">
      <div class="gc-stat-label">GPA (4.0 scale)</div>
      <div class="gc-stat-value" id="gc-gpa" style="color:#6366f1;">—</div>
      <div class="gc-stat-sub">standard 4.0 scale</div>
    </div>
    <div class="gc-stat">
      <div class="gc-stat-label">Points Scored</div>
      <div class="gc-stat-value" id="gc-points" style="color:#475569; font-size:1.2rem;">—</div>
      <div class="gc-stat-sub">score / max score</div>
    </div>
  </div>
  <div class="gc-gpa-scale" id="gc-gpa-scale"></div>
</div>

<!-- Final Exam Calculator -->
<div class="gc-card">
  <div class="gc-card-title"><span class="icon">🎯</span> "What Do I Need on My Final?" Calculator</div>
  <div class="gc-final-grid">
    <div>
      <label style="font-size:0.875rem;font-weight:600;color:#475569;">Final Exam Weight in Course (%)</label>
      <div class="gc-final-input-row" style="margin-top:8px;">
        <input type="number" id="gc-final-weight" min="0" max="100" value="30" oninput="gcCalcFinal()" placeholder="e.g. 30">
        <span style="font-size:0.85rem;color:#666;">% of total grade</span>
      </div>
    </div>
    <div>
      <label style="font-size:0.875rem;font-weight:600;color:#475569;">Desired Final Grade</label>
      <div class="gc-final-input-row" style="margin-top:8px;">
        <select id="gc-target-grade" onchange="gcCalcFinal()">
          <option value="97">A+ (97%)</option>
          <option value="93">A (93%)</option>
          <option value="90">A- (90%)</option>
          <option value="87">B+ (87%)</option>
          <option value="83" selected>B (83%)</option>
          <option value="80">B- (80%)</option>
          <option value="77">C+ (77%)</option>
          <option value="73">C (73%)</option>
          <option value="70">C- (70%)</option>
          <option value="67">D+ (67%)</option>
          <option value="60">D (60%)</option>
        </select>
      </div>
    </div>
  </div>
  <div id="gc-final-result" class="gc-final-result" style="display:none;"></div>
</div>

<!-- Related Tools -->
<div class="gc-related">
  <h3>Related Free Tools</h3>
  <ul>
    <li><a href="/tools/gpa-calculator/">GPA Calculator</a> — Convert letter grades to GPA across multiple courses</li>
    <li><a href="/tools/percentage-calculator/">Percentage Calculator</a> — Quick percent change, of, and off calculations</li>
    <li><a href="/tools/study-timer/">Study Timer (Pomodoro)</a> — Focus sessions with automatic break reminders</li>
    <li><a href="/tools/unit-converter/">Unit Converter</a> — Length, weight, temperature, and more</li>
  </ul>
</div>

<script>
(function() {
  var gcRows = [];
  var gcIdCounter = 0;

  var GRADES = [
    { label: "A+", min: 97, gpa: 4.0, cls: "Aplus" },
    { label: "A",  min: 93, gpa: 4.0, cls: "A" },
    { label: "A-", min: 90, gpa: 3.7, cls: "Aminus" },
    { label: "B+", min: 87, gpa: 3.3, cls: "Bplus" },
    { label: "B",  min: 83, gpa: 3.0, cls: "B" },
    { label: "B-", min: 80, gpa: 2.7, cls: "Bminus" },
    { label: "C+", min: 77, gpa: 2.3, cls: "Cplus" },
    { label: "C",  min: 73, gpa: 2.0, cls: "C" },
    { label: "C-", min: 70, gpa: 1.7, cls: "Cminus" },
    { label: "D+", min: 67, gpa: 1.3, cls: "Dplus" },
    { label: "D",  min: 60, gpa: 1.0, cls: "D" },
    { label: "F",  min: 0,  gpa: 0.0, cls: "F" }
  ];

  function getGradeInfo(pct) {
    for (var i = 0; i < GRADES.length; i++) {
      if (pct >= GRADES[i].min) return GRADES[i];
    }
    return GRADES[GRADES.length - 1];
  }

  function gcAddRow(name, score, max, weight) {
    var id = ++gcIdCounter;
    gcRows.push({ id: id });
    renderTable();
    if (name !== undefined) {
      document.getElementById("gc-name-" + id).value = name || "";
      document.getElementById("gc-score-" + id).value = score !== undefined ? score : "";
      document.getElementById("gc-max-" + id).value = max !== undefined ? max : "100";
      document.getElementById("gc-weight-" + id).value = weight !== undefined ? weight : "";
    }
    gcUpdate();
  }
  window.gcAddRow = function() { gcAddRow(); };

  function gcRemoveRow(id) {
    gcRows = gcRows.filter(function(r) { return r.id !== id; });
    renderTable();
    gcUpdate();
  }

  function renderTable() {
    var tbody = document.getElementById("gc-tbody");
    if (gcRows.length === 0) {
      tbody.innerHTML = '<tr class="gc-empty-row"><td colspan="7">No assignments yet. Click "+ Add Assignment" to get started.</td></tr>';
      return;
    }
    tbody.innerHTML = gcRows.map(function(r) {
      return '<tr id="gc-row-' + r.id + '">' +
        '<td><input type="text" id="gc-name-' + r.id + '" placeholder="e.g. Midterm Exam" oninput="gcUpdate()"></td>' +
        '<td><input type="number" id="gc-score-' + r.id + '" placeholder="85" min="0" oninput="gcUpdate()"></td>' +
        '<td><input type="number" id="gc-max-' + r.id + '" placeholder="100" min="1" value="100" oninput="gcUpdate()"></td>' +
        '<td><input type="number" id="gc-weight-' + r.id + '" placeholder="20" min="0" max="100" oninput="gcUpdate()"></td>' +
        '<td class="gc-grade-cell" id="gc-grade-' + r.id + '">—</td>' +
        '<td class="gc-pct" id="gc-pct-' + r.id + '">—</td>' +
        '<td><button class="gc-btn-remove" onclick="gcRemoveRow(' + r.id + ')" title="Remove">&#x2715;</button></td>' +
      '</tr>';
    }).join("");
  }

  function gcUpdate() {
    var totalWeight = 0;
    var weightedSum = 0;
    var totalScore = 0;
    var totalMax = 0;
    var hasAny = false;

    gcRows.forEach(function(r) {
      var scoreEl = document.getElementById("gc-score-" + r.id);
      var maxEl   = document.getElementById("gc-max-" + r.id);
      var wEl     = document.getElementById("gc-weight-" + r.id);
      var gradeEl = document.getElementById("gc-grade-" + r.id);
      var pctEl   = document.getElementById("gc-pct-" + r.id);

      if (!scoreEl) return;
      var score  = parseFloat(scoreEl.value);
      var max    = parseFloat(maxEl.value) || 100;
      var weight = parseFloat(wEl.value);

      if (!isNaN(weight) && weight > 0) totalWeight += weight;

      if (!isNaN(score) && !isNaN(max) && max > 0) {
        var pct = (score / max) * 100;
        var gi  = getGradeInfo(pct);
        pctEl.textContent = pct.toFixed(1) + "%";
        gradeEl.innerHTML = '<span class="gc-grade-badge grade-' + gi.cls + '">' + gi.label + '</span>';
        totalScore += score;
        totalMax   += max;
        if (!isNaN(weight) && weight > 0) {
          weightedSum += (pct / 100) * weight;
          hasAny = true;
        }
      } else {
        pctEl.textContent = "—";
        gradeEl.innerHTML = "—";
      }
    });

    // Weight bar
    var fill = document.getElementById("gc-weight-fill");
    var wlabel = document.getElementById("gc-weight-label");
    var pctFill = Math.min(totalWeight, 100);
    fill.style.width = pctFill + "%";

    var alertEl = document.getElementById("gc-weight-alert");
    if (totalWeight === 0) {
      fill.style.background = "#cbd5e1";
      wlabel.style.color = "#94a3b8";
      wlabel.textContent = "Total: 0%";
      alertEl.innerHTML = "";
    } else if (Math.abs(totalWeight - 100) < 0.01) {
      fill.style.background = "#16a34a";
      wlabel.style.color = "#16a34a";
      wlabel.textContent = "Total: 100% \u2713";
      alertEl.innerHTML = '<div class="gc-alert gc-alert-ok">Weights sum to 100% — your weighted average is accurate.</div>';
    } else if (totalWeight > 100) {
      fill.style.background = "#ef4444";
      wlabel.style.color = "#ef4444";
      wlabel.textContent = "Total: " + totalWeight.toFixed(1) + "% \u26A0";
      alertEl.innerHTML = '<div class="gc-alert gc-alert-err">Weights exceed 100% by ' + (totalWeight - 100).toFixed(1) + '%. Please adjust.</div>';
    } else {
      fill.style.background = "#f59e0b";
      wlabel.style.color = "#d97706";
      wlabel.textContent = "Total: " + totalWeight.toFixed(1) + "%";
      alertEl.innerHTML = '<div class="gc-alert gc-alert-warn">Weights sum to ' + totalWeight.toFixed(1) + '%. Add ' + (100 - totalWeight).toFixed(1) + '% more for a complete weighted average.</div>';
    }

    // Summary
    var wavgEl   = document.getElementById("gc-wavg");
    var letterEl = document.getElementById("gc-letter");
    var letterSub = document.getElementById("gc-letter-sub");
    var gpaEl    = document.getElementById("gc-gpa");
    var pointsEl = document.getElementById("gc-points");

    if (hasAny && totalWeight > 0) {
      var normalizedAvg = (weightedSum / totalWeight) * 100;
      var gi = getGradeInfo(normalizedAvg);
      wavgEl.textContent = normalizedAvg.toFixed(2) + "%";
      wavgEl.style.color = gradeColor(gi.cls);
      letterEl.innerHTML = '<span class="gc-grade-badge grade-' + gi.cls + '" style="font-size:1.8rem;padding:4px 14px;">' + gi.label + '</span>';
      letterSub.textContent = gi.label + " — " + normalizedAvg.toFixed(1) + "%";
      gpaEl.textContent = gi.gpa.toFixed(1);
      gpaEl.style.color = gradeColor(gi.cls);
    } else if (totalMax > 0) {
      var rawPct = (totalScore / totalMax) * 100;
      var gi2 = getGradeInfo(rawPct);
      wavgEl.textContent = rawPct.toFixed(2) + "%";
      wavgEl.style.color = gradeColor(gi2.cls);
      letterEl.innerHTML = '<span class="gc-grade-badge grade-' + gi2.cls + '" style="font-size:1.8rem;padding:4px 14px;">' + gi2.label + '</span>';
      letterSub.textContent = "Raw (no weights set)";
      gpaEl.textContent = gi2.gpa.toFixed(1);
      gpaEl.style.color = gradeColor(gi2.cls);
    } else {
      wavgEl.textContent = "—";
      wavgEl.style.color = "#6366f1";
      letterEl.innerHTML = "—";
      letterSub.textContent = "";
      gpaEl.textContent = "—";
      gpaEl.style.color = "#6366f1";
    }

    if (totalMax > 0) {
      pointsEl.textContent = totalScore.toFixed(1) + " / " + totalMax.toFixed(1);
    } else {
      pointsEl.textContent = "—";
    }

    // GPA chips
    var chipWrap = document.getElementById("gc-gpa-scale");
    var currentGpa = hasAny && totalWeight > 0
      ? getGradeInfo((weightedSum / totalWeight) * 100).gpa
      : (totalMax > 0 ? getGradeInfo((totalScore / totalMax) * 100).gpa : null);
    chipWrap.innerHTML = GRADES.map(function(g) {
      var active = currentGpa !== null && g.gpa === currentGpa && g.cls === (hasAny && totalWeight > 0 ? getGradeInfo((weightedSum / totalWeight) * 100).cls : (totalMax > 0 ? getGradeInfo((totalScore / totalMax) * 100).cls : "")) ? " active" : "";
      return '<span class="gc-gpa-chip' + active + '">' + g.label + ' = ' + g.gpa.toFixed(1) + '</span>';
    }).join("");

    gcCalcFinal();
  }

  function gradeColor(cls) {
    if (cls.startsWith("A")) return "#16a34a";
    if (cls.startsWith("B")) return "#2563eb";
    if (cls.startsWith("C")) return "#d97706";
    if (cls.startsWith("D")) return "#ea580c";
    return "#dc2626";
  }

  function gcCalcFinal() {
    var finalWeightEl = document.getElementById("gc-final-weight");
    var targetEl = document.getElementById("gc-target-grade");
    var resultEl = document.getElementById("gc-final-result");

    var finalWeight = parseFloat(finalWeightEl.value) / 100;
    var target = parseFloat(targetEl.value) / 100;
    if (isNaN(finalWeight) || finalWeight <= 0 || isNaN(target)) {
      resultEl.style.display = "none";
      return;
    }

    // Get current weighted avg (without final)
    var totalWeight = 0;
    var weightedSum = 0;
    var hasAny = false;
    gcRows.forEach(function(r) {
      var scoreEl = document.getElementById("gc-score-" + r.id);
      var maxEl   = document.getElementById("gc-max-" + r.id);
      var wEl     = document.getElementById("gc-weight-" + r.id);
      if (!scoreEl) return;
      var score  = parseFloat(scoreEl.value);
      var max    = parseFloat(maxEl.value) || 100;
      var weight = parseFloat(wEl.value);
      if (!isNaN(score) && !isNaN(max) && max > 0 && !isNaN(weight) && weight > 0) {
        var pct = score / max;
        weightedSum += pct * weight;
        totalWeight += weight;
        hasAny = true;
      }
    });

    var currentNormWeight = totalWeight / 100;
    var currentAvg = hasAny ? (weightedSum / 100) : null;

    // Formula: target = currentAvg * (1 - finalWeight) + finalScore * finalWeight
    // finalScore = (target - currentAvg * (1 - finalWeight)) / finalWeight
    var resultEl2 = document.getElementById("gc-final-result");
    resultEl2.style.display = "block";

    if (currentAvg === null) {
      resultEl2.innerHTML = "Enter your assignment scores and weights above to calculate what you need on your final.";
      return;
    }

    var needed = (target - currentAvg * (1 - finalWeight)) / finalWeight;
    var neededPct = needed * 100;
    var targetGi = getGradeInfo(parseFloat(targetEl.value));

    if (neededPct > 100) {
      resultEl2.innerHTML = 'To achieve <strong>' + targetGi.label + ' (' + targetEl.value + '%)</strong>, you would need <strong>' + neededPct.toFixed(1) + '%</strong> on your final exam — which exceeds 100%. Consider a lower target grade or contact your professor about extra credit.';
    } else if (neededPct < 0) {
      resultEl2.innerHTML = 'Great news! You already have <strong>' + targetGi.label + '</strong> locked in — even scoring 0% on your final, you\'ll still achieve your target. You need at least <strong>0%</strong> on the final.';
    } else {
      var neededGi = getGradeInfo(neededPct);
      resultEl2.innerHTML = 'To achieve <strong>' + targetGi.label + ' (' + targetEl.value + '%)</strong> in this course, you need at least <strong>' + neededPct.toFixed(1) + '% (<span class="gc-grade-badge grade-' + neededGi.cls + '">' + neededGi.label + '</span>)</strong> on your final exam (worth ' + (finalWeight * 100).toFixed(0) + '% of your grade).';
    }
  }
  window.gcCalcFinal = gcCalcFinal;

  function gcReset() {
    gcRows = [];
    gcIdCounter = 0;
    renderTable();
    gcUpdate();
  }
  window.gcReset = gcReset;

  window.gcRemoveRow = gcRemoveRow;

  // Seed with sample data
  gcAddRow("Homework Average", 88, 100, 20);
  gcAddRow("Midterm Exam", 76, 100, 25);
  gcAddRow("Lab Reports", 92, 100, 15);
  gcAddRow("Quizzes", 84, 100, 10);
  // Final exam slot intentionally blank — user fills in
})();
</script>
</div>
