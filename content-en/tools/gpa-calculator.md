---
title: "GPA Calculator"
description: "Free GPA calculator. Calculate your Grade Point Average with custom grading scales. Supports 4.0 and 5.0 scales, weighted GPA, semester and cumulative GPA."
slug: gpa-calculator
date: 2025-05-16
categories: ["Free Tools"]
tags: ["Calculator", "Converter", "Free Tools"]
ShowToc: false
cover:
  image: /images/covers/gpa-calculator.png
  alt: "GPA Calculator"
---

<div id="gp-app">

<style>
#gp-app * { box-sizing: border-box; margin: 0; padding: 0; }
#gp-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
max-width: 680px;
margin: 0 auto;
padding: 16px;
color: #1e293b;
}

/* Controls bar */
#gp-app .gp-controls {
display: flex;
flex-wrap: wrap;
gap: 10px;
align-items: center;
margin-bottom: 18px;
}
#gp-app .gp-scale-group,
#gp-app .gp-weighted-group {
display: flex;
align-items: center;
gap: 8px;
background: #f1f5f9;
border-radius: 8px;
padding: 8px 14px;
}
#gp-app .gp-controls label {
font-size: 13px;
font-weight: 600;
color: #475569;
}
#gp-app .gp-scale-btn {
padding: 5px 14px;
border-radius: 6px;
border: 1.5px solid #cbd5e1;
background: #fff;
color: #475569;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
}
#gp-app .gp-scale-btn.active {
background: #2563eb;
border-color: #2563eb;
color: #fff;
}
#gp-app .gp-scale-btn:hover:not(.active) {
border-color: #93c5fd;
color: #2563eb;
}
#gp-app .gp-toggle {
position: relative;
width: 40px;
height: 22px;
cursor: pointer;
}
#gp-app .gp-toggle input { opacity: 0; width: 0; height: 0; position: absolute; }
#gp-app .gp-toggle-track {
position: absolute;
inset: 0;
border-radius: 22px;
background: #cbd5e1;
transition: background 0.2s;
}
#gp-app .gp-toggle input:checked + .gp-toggle-track { background: #2563eb; }
#gp-app .gp-toggle-thumb {
position: absolute;
top: 3px;
left: 3px;
width: 16px;
height: 16px;
border-radius: 50%;
background: #fff;
transition: left 0.2s;
box-shadow: 0 1px 3px rgba(0,0,0,0.2);
}
#gp-app .gp-toggle input:checked ~ .gp-toggle-thumb { left: 21px; }

/* Course table */
#gp-app .gp-table-wrap {
background: #fff;
border: 1.5px solid #e2e8f0;
border-radius: 12px;
overflow: hidden;
margin-bottom: 16px;
}
#gp-app .gp-thead {
display: grid;
grid-template-columns: 1fr 90px 110px 44px;
background: #f8fafc;
border-bottom: 1.5px solid #e2e8f0;
padding: 10px 14px;
gap: 8px;
}
#gp-app .gp-thead span {
font-size: 12px;
font-weight: 700;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.06em;
}
#gp-app .gp-course-list { list-style: none; }
#gp-app .gp-course-row {
display: grid;
grid-template-columns: 1fr 90px 110px 44px;
gap: 8px;
padding: 10px 14px;
border-bottom: 1px solid #f1f5f9;
align-items: center;
transition: background 0.1s;
}
#gp-app .gp-course-row:last-child { border-bottom: none; }
#gp-app .gp-course-row:hover { background: #fafbff; }
#gp-app .gp-input {
width: 100%;
border: 1.5px solid #e2e8f0;
border-radius: 6px;
padding: 6px 10px;
font-size: 14px;
color: #1e293b;
background: #fff;
transition: border-color 0.15s;
-webkit-appearance: none;
}
#gp-app .gp-input:focus {
outline: none;
border-color: #3b82f6;
box-shadow: 0 0 0 3px rgba(59,130,246,0.12);
}
#gp-app select.gp-input { cursor: pointer; }
#gp-app .gp-remove-btn {
width: 28px;
height: 28px;
border: none;
border-radius: 6px;
background: #fee2e2;
color: #dc2626;
font-size: 16px;
cursor: pointer;
display: flex;
align-items: center;
justify-content: center;
transition: background 0.15s;
line-height: 1;
justify-self: center;
}
#gp-app .gp-remove-btn:hover { background: #fecaca; }

/* Add course button */
#gp-app .gp-add-btn {
width: 100%;
padding: 10px;
border: 1.5px dashed #93c5fd;
border-radius: 8px;
background: #eff6ff;
color: #2563eb;
font-size: 14px;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
margin-bottom: 20px;
}
#gp-app .gp-add-btn:hover {
background: #dbeafe;
border-color: #3b82f6;
}

/* Results panel */
#gp-app .gp-results {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 12px;
margin-bottom: 20px;
}
#gp-app .gp-result-card {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 12px;
padding: 16px 14px;
text-align: center;
}
#gp-app .gp-result-card.highlight {
background: linear-gradient(135deg, #eff6ff 0%, #dbeafe 100%);
border-color: #93c5fd;
}
#gp-app .gp-result-label {
font-size: 11px;
font-weight: 700;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.07em;
margin-bottom: 6px;
}
#gp-app .gp-result-value {
font-size: 28px;
font-weight: 700;
color: #1e293b;
line-height: 1.1;
}
#gp-app .gp-result-card.highlight .gp-result-value { color: #1d4ed8; }
#gp-app .gp-result-sub {
font-size: 12px;
color: #94a3b8;
margin-top: 4px;
}

/* Grade scale reference */
#gp-app .gp-scale-ref {
background: #f8fafc;
border: 1.5px solid #e2e8f0;
border-radius: 10px;
padding: 14px 16px;
margin-bottom: 20px;
}
#gp-app .gp-scale-ref h3 {
font-size: 12px;
font-weight: 700;
color: #64748b;
text-transform: uppercase;
letter-spacing: 0.06em;
margin-bottom: 10px;
}
#gp-app .gp-scale-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(80px, 1fr));
gap: 6px;
}
#gp-app .gp-scale-item {
background: #fff;
border: 1px solid #e2e8f0;
border-radius: 6px;
padding: 5px 8px;
text-align: center;
font-size: 12px;
}
#gp-app .gp-scale-item .si-grade { font-weight: 700; color: #1e293b; }
#gp-app .gp-scale-item .si-points { color: #2563eb; font-weight: 600; }

/* Reset btn */
#gp-app .gp-reset-btn {
display: block;
margin: 0 auto 20px;
padding: 9px 24px;
border: 1.5px solid #e2e8f0;
border-radius: 8px;
background: #fff;
color: #64748b;
font-size: 13px;
font-weight: 600;
cursor: pointer;
transition: all 0.15s;
}
#gp-app .gp-reset-btn:hover { border-color: #94a3b8; color: #334155; }

/* Cross-links */
#gp-app .gp-crosslinks {
margin-top: 20px;
font-size: 13px;
color: #6c757d;
line-height: 1.8;
}
#gp-app .gp-crosslinks a { color: #2563eb; text-decoration: none; }
#gp-app .gp-crosslinks a:hover { text-decoration: underline; }

/* Mobile */
@media (max-width: 520px) {
#gp-app .gp-results { grid-template-columns: 1fr 1fr; }
#gp-app .gp-result-card:first-child { grid-column: span 2; }
#gp-app .gp-thead,
#gp-app .gp-course-row { grid-template-columns: 1fr 72px 96px 36px; gap: 6px; padding: 8px 10px; }
#gp-app .gp-result-value { font-size: 22px; }
}
</style>

<!-- Controls -->
<div class="gp-controls">
<div class="gp-scale-group">
<label>Scale:</label>
<button class="gp-scale-btn active" id="gp-btn-40" onclick="gpSetScale(4.0)">4.0</button>
<button class="gp-scale-btn" id="gp-btn-50" onclick="gpSetScale(5.0)">5.0</button>
</div>
<div class="gp-weighted-group">
<label for="gp-weighted-toggle">Weighted</label>
<label class="gp-toggle">
<input type="checkbox" id="gp-weighted-toggle" onchange="gpRecalc()">
<span class="gp-toggle-track"></span>
<span class="gp-toggle-thumb"></span>
</label>
</div>
</div>

<!-- Results -->
<div class="gp-results">
<div class="gp-result-card highlight">
<div class="gp-result-label">Semester GPA</div>
<div class="gp-result-value" id="gp-sem-gpa">—</div>
<div class="gp-result-sub" id="gp-scale-label">/ 4.0 scale</div>
</div>
<div class="gp-result-card">
<div class="gp-result-label">Total Credits</div>
<div class="gp-result-value" id="gp-total-credits">0</div>
<div class="gp-result-sub">credit hours</div>
</div>
<div class="gp-result-card">
<div class="gp-result-label">Quality Points</div>
<div class="gp-result-value" id="gp-quality-pts">0</div>
<div class="gp-result-sub">grade × credits</div>
</div>
</div>

<!-- Course table -->
<div class="gp-table-wrap">
<div class="gp-thead">
<span>Course Name</span>
<span>Credits</span>
<span>Grade</span>
<span></span>
</div>
<ul class="gp-course-list" id="gp-course-list"></ul>
</div>

<button class="gp-add-btn" onclick="gpAddCourse()">+ Add Course</button>

<!-- Grade scale reference -->
<div class="gp-scale-ref">
<h3>Grade Scale Reference</h3>
<div class="gp-scale-grid" id="gp-scale-grid"></div>
</div>

<button class="gp-reset-btn" onclick="gpReset()">Reset All</button>

<div class="gp-crosslinks">
Calculate percentages &rarr; <a href="/tools/percentage-calculator/">Percentage Calculator</a><br>
Advanced math &rarr; <a href="/tools/scientific-calculator/">Scientific Calculator</a>
</div>

</div>

<script>
(function() {
'use strict';

var GP = {
scale: 4.0,
weighted: false,
courses: [],
nextId: 1
};

var GRADES_40 = [
{ label: 'A+', points: 4.0 },
{ label: 'A',  points: 4.0 },
{ label: 'A-', points: 3.7 },
{ label: 'B+', points: 3.3 },
{ label: 'B',  points: 3.0 },
{ label: 'B-', points: 2.7 },
{ label: 'C+', points: 2.3 },
{ label: 'C',  points: 2.0 },
{ label: 'C-', points: 1.7 },
{ label: 'D+', points: 1.3 },
{ label: 'D',  points: 1.0 },
{ label: 'D-', points: 0.7 },
{ label: 'F',  points: 0.0 }
];

var GRADES_50 = [
{ label: 'A+', points: 5.0 },
{ label: 'A',  points: 5.0 },
{ label: 'A-', points: 4.7 },
{ label: 'B+', points: 4.3 },
{ label: 'B',  points: 4.0 },
{ label: 'B-', points: 3.7 },
{ label: 'C+', points: 3.3 },
{ label: 'C',  points: 3.0 },
{ label: 'C-', points: 2.7 },
{ label: 'D+', points: 2.3 },
{ label: 'D',  points: 2.0 },
{ label: 'D-', points: 1.7 },
{ label: 'F',  points: 0.0 }
];

function currentGrades() {
return GP.scale === 5.0 ? GRADES_50 : GRADES_40;
}

function gradeOptions() {
return currentGrades().map(function(g) {
return '<option value="' + g.label + '">' + g.label + ' (' + g.points.toFixed(1) + ')</option>';
}).join('');
}

function pointsForGrade(label) {
var grades = currentGrades();
for (var i = 0; i < grades.length; i++) {
if (grades[i].label === label) return grades[i].points;
}
return 0;
}

function renderCourseList() {
var ul = document.getElementById('gp-course-list');
if (!GP.courses.length) {
ul.innerHTML = '<li style="padding:16px 14px;font-size:13px;color:#94a3b8;text-align:center;">No courses added yet. Click &ldquo;+ Add Course&rdquo; below.</li>';
return;
}
ul.innerHTML = GP.courses.map(function(c) {
return '<li class="gp-course-row" id="gp-row-' + c.id + '">' +
'<input class="gp-input" type="text" placeholder="e.g. Mathematics" value="' + escAttr(c.name) + '" ' +
'onchange="gpUpdateField(' + c.id + ',\'name\',this.value)" ' +
'oninput="gpUpdateField(' + c.id + ',\'name\',this.value)">' +
'<input class="gp-input" type="number" min="0.5" max="12" step="0.5" value="' + c.credits + '" ' +
'onchange="gpUpdateField(' + c.id + ',\'credits\',this.value)" ' +
'oninput="gpUpdateField(' + c.id + ',\'credits\',this.value)">' +
'<select class="gp-input" onchange="gpUpdateField(' + c.id + ',\'grade\',this.value)">' +
gradeOptionsSelected(c.grade) +
'</select>' +
'<button class="gp-remove-btn" onclick="gpRemoveCourse(' + c.id + ')" title="Remove">&#x2715;</button>' +
'</li>';
}).join('');
}

function gradeOptionsSelected(selected) {
return currentGrades().map(function(g) {
var sel = (g.label === selected) ? ' selected' : '';
return '<option value="' + g.label + '"' + sel + '>' + g.label + ' (' + g.points.toFixed(1) + ')</option>';
}).join('');
}

function renderScaleRef() {
var grades = currentGrades();
var grid = document.getElementById('gp-scale-grid');
grid.innerHTML = grades.map(function(g) {
return '<div class="gp-scale-item">' +
'<div class="si-grade">' + g.label + '</div>' +
'<div class="si-points">' + g.points.toFixed(1) + '</div>' +
'</div>';
}).join('');
}

function gpRecalcInternal() {
GP.weighted = document.getElementById('gp-weighted-toggle').checked;
var totalCredits = 0;
var totalQP = 0;
var valid = 0;

GP.courses.forEach(function(c) {
var cr = parseFloat(c.credits);
if (isNaN(cr) || cr <= 0) return;
var pts = pointsForGrade(c.grade);
if (GP.weighted) {
// Weighted: treat credits as weight multiplier
totalQP += pts * cr;
totalCredits += cr;
} else {
totalQP += pts * cr;
totalCredits += cr;
}
valid++;
});

var semGpa = (totalCredits > 0) ? (totalQP / totalCredits) : null;

document.getElementById('gp-sem-gpa').textContent = semGpa !== null ? semGpa.toFixed(2) : '—';
document.getElementById('gp-total-credits').textContent = totalCredits % 1 === 0 ? totalCredits : totalCredits.toFixed(1);
document.getElementById('gp-quality-pts').textContent = totalQP % 1 === 0 ? totalQP : totalQP.toFixed(2);
document.getElementById('gp-scale-label').textContent = '/ ' + GP.scale.toFixed(1) + ' scale';
}

window.gpRecalc = function() {
gpRecalcInternal();
};

window.gpSetScale = function(scale) {
GP.scale = scale;
document.getElementById('gp-btn-40').classList.toggle('active', scale === 4.0);
document.getElementById('gp-btn-50').classList.toggle('active', scale === 5.0);
// Re-map current grade labels to new scale defaults (keep letter grades, recalc points)
renderCourseList();
renderScaleRef();
gpRecalcInternal();
};

window.gpAddCourse = function() {
var grades = currentGrades();
GP.courses.push({ id: GP.nextId++, name: '', credits: 3, grade: grades[1].label });
renderCourseList();
gpRecalcInternal();
// Focus the new name input
var rows = document.querySelectorAll('.gp-course-row');
if (rows.length) {
var lastInput = rows[rows.length - 1].querySelector('input[type="text"]');
if (lastInput) lastInput.focus();
}
};

window.gpRemoveCourse = function(id) {
GP.courses = GP.courses.filter(function(c) { return c.id !== id; });
renderCourseList();
gpRecalcInternal();
};

window.gpUpdateField = function(id, field, value) {
var course = null;
for (var i = 0; i < GP.courses.length; i++) {
if (GP.courses[i].id === id) { course = GP.courses[i]; break; }
}
if (!course) return;
if (field === 'credits') {
course.credits = parseFloat(value) || 0;
} else {
course[field] = value;
}
gpRecalcInternal();
};

window.gpReset = function() {
GP.courses = [];
GP.nextId = 1;
GP.scale = 4.0;
GP.weighted = false;
document.getElementById('gp-weighted-toggle').checked = false;
document.getElementById('gp-btn-40').classList.add('active');
document.getElementById('gp-btn-50').classList.remove('active');
renderCourseList();
renderScaleRef();
gpRecalcInternal();
};

function escAttr(s) {
return String(s).replace(/&/g,'&amp;').replace(/"/g,'&quot;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

// Init with 3 default courses
var initGrades = currentGrades();
GP.courses = [
{ id: GP.nextId++, name: 'Introduction to Computer Science', credits: 3, grade: initGrades[1].label },
{ id: GP.nextId++, name: 'Calculus I',                       credits: 4, grade: initGrades[4].label },
{ id: GP.nextId++, name: 'English Composition',              credits: 3, grade: initGrades[2].label }
];
renderCourseList();
renderScaleRef();
gpRecalcInternal();

})();
</script>
</div>
