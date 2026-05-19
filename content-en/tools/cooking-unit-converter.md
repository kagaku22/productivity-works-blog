---
title: "Cooking Unit Converter - Kitchen Measurement Calculator"
date: 2025-05-16
description: "Convert cooking measurements between cups, tablespoons, teaspoons, ml, grams, ounces. Recipe scaling and ingredient converter."
categories: ["Free Tools"]
slug: "cooking-unit-converter"
ShowToc: false
cover:
  image: "/images/covers/cooking-unit-converter.png"
  alt: "Cooking Unit Converter"
---

<div id="cu-app">

<style>
#cu-app {
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
max-width: 820px;
margin: 0 auto;
color: #1a1a2e;
line-height: 1.6;
}
#cu-app h2 {
font-size: 1.4rem;
font-weight: 700;
color: #1a1a2e;
margin: 1.8rem 0 1rem;
padding-bottom: 0.4rem;
border-bottom: 2px solid #f0a500;
}
#cu-app .tabs {
display: flex;
gap: 0.5rem;
margin-bottom: 1.5rem;
flex-wrap: wrap;
}
#cu-app .tab-btn {
padding: 0.55rem 1.2rem;
border: 2px solid #e0e0e0;
border-radius: 2rem;
background: #fff;
color: #555;
font-size: 0.9rem;
font-weight: 600;
cursor: pointer;
transition: all 0.2s;
}
#cu-app .tab-btn.active,
#cu-app .tab-btn:hover {
background: #f0a500;
border-color: #f0a500;
color: #fff;
}
#cu-app .panel {
display: none;
background: #fff;
border: 1px solid #e8e8e8;
border-radius: 12px;
padding: 1.5rem;
box-shadow: 0 2px 8px rgba(0,0,0,0.06);
}
#cu-app .panel.active {
display: block;
}
#cu-app .converter-grid {
display: grid;
grid-template-columns: 1fr auto 1fr;
gap: 1rem;
align-items: end;
margin-bottom: 1rem;
}
#cu-app .swap-btn {
background: #f0a500;
color: #fff;
border: none;
border-radius: 50%;
width: 40px;
height: 40px;
font-size: 1.1rem;
cursor: pointer;
transition: background 0.2s;
display: flex;
align-items: center;
justify-content: center;
margin-bottom: 0.2rem;
}
#cu-app .swap-btn:hover { background: #d4920a; }
#cu-app label {
display: block;
font-size: 0.82rem;
font-weight: 600;
color: #666;
margin-bottom: 0.3rem;
text-transform: uppercase;
letter-spacing: 0.03em;
}
#cu-app input[type="number"],
#cu-app select {
width: 100%;
padding: 0.65rem 0.8rem;
border: 1.5px solid #ddd;
border-radius: 8px;
font-size: 1rem;
background: #fafafa;
box-sizing: border-box;
transition: border-color 0.2s;
}
#cu-app input[type="number"]:focus,
#cu-app select:focus {
outline: none;
border-color: #f0a500;
background: #fff;
}
#cu-app .result-box {
background: linear-gradient(135deg, #fff7e6, #fff);
border: 1.5px solid #f0a500;
border-radius: 10px;
padding: 1rem 1.2rem;
margin-top: 1rem;
text-align: center;
}
#cu-app .result-box .result-value {
font-size: 2rem;
font-weight: 800;
color: #f0a500;
}
#cu-app .result-box .result-label {
font-size: 0.9rem;
color: #888;
margin-top: 0.2rem;
}
#cu-app .ingredient-row {
display: flex;
gap: 0.8rem;
margin-bottom: 1rem;
align-items: end;
flex-wrap: wrap;
}
#cu-app .ingredient-row > div {
flex: 1;
min-width: 120px;
}
#cu-app .scaler-row {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 1rem;
margin-bottom: 1rem;
}
#cu-app .scaler-ingredients {
margin-top: 1rem;
}
#cu-app .scaler-ingredient-item {
display: grid;
grid-template-columns: 1fr 1fr auto;
gap: 0.6rem;
margin-bottom: 0.5rem;
align-items: center;
}
#cu-app .scaler-ingredient-item input,
#cu-app .scaler-ingredient-item select {
padding: 0.5rem 0.6rem;
font-size: 0.9rem;
}
#cu-app .remove-btn {
background: #ff5555;
color: #fff;
border: none;
border-radius: 6px;
padding: 0.5rem 0.7rem;
cursor: pointer;
font-size: 0.85rem;
}
#cu-app .remove-btn:hover { background: #cc3333; }
#cu-app .add-btn {
background: #e8f5e9;
color: #2e7d32;
border: 1.5px solid #a5d6a7;
border-radius: 8px;
padding: 0.5rem 1rem;
cursor: pointer;
font-size: 0.88rem;
font-weight: 600;
margin-right: 0.5rem;
}
#cu-app .add-btn:hover { background: #c8e6c9; }
#cu-app .calc-btn {
background: #f0a500;
color: #fff;
border: none;
border-radius: 8px;
padding: 0.55rem 1.2rem;
cursor: pointer;
font-size: 0.9rem;
font-weight: 700;
}
#cu-app .calc-btn:hover { background: #d4920a; }
#cu-app .scaler-result {
background: #f8f9fa;
border-radius: 10px;
padding: 1rem;
margin-top: 1rem;
}
#cu-app .scaler-result table {
width: 100%;
border-collapse: collapse;
font-size: 0.92rem;
}
#cu-app .scaler-result th {
text-align: left;
padding: 0.4rem 0.6rem;
background: #f0a500;
color: #fff;
border-radius: 4px;
}
#cu-app .scaler-result td {
padding: 0.4rem 0.6rem;
border-bottom: 1px solid #eee;
}
#cu-app .scaler-result tr:last-child td { border-bottom: none; }
#cu-app .ref-table {
width: 100%;
border-collapse: collapse;
font-size: 0.88rem;
margin-top: 0.5rem;
}
#cu-app .ref-table th {
background: #1a1a2e;
color: #fff;
padding: 0.55rem 0.8rem;
text-align: left;
}
#cu-app .ref-table td {
padding: 0.5rem 0.8rem;
border-bottom: 1px solid #eee;
}
#cu-app .ref-table tr:nth-child(even) td { background: #f9f9f9; }
#cu-app .tip-box {
background: #e8f4fd;
border-left: 4px solid #2196f3;
border-radius: 0 8px 8px 0;
padding: 0.8rem 1rem;
margin: 1rem 0;
font-size: 0.88rem;
color: #1565c0;
}
#cu-app .related-tools {
background: #f8f9fa;
border-radius: 10px;
padding: 1.2rem;
margin-top: 2rem;
}
#cu-app .related-tools h3 {
margin: 0 0 0.8rem;
font-size: 1rem;
color: #1a1a2e;
}
#cu-app .related-tools ul {
margin: 0;
padding-left: 1.2rem;
}
#cu-app .related-tools li {
margin-bottom: 0.4rem;
font-size: 0.9rem;
}
#cu-app .related-tools a {
color: #f0a500;
text-decoration: none;
font-weight: 600;
}
#cu-app .related-tools a:hover { text-decoration: underline; }
@media (max-width: 600px) {
#cu-app .converter-grid {
grid-template-columns: 1fr;
}
#cu-app .swap-btn {
margin: 0 auto;
transform: rotate(90deg);
}
#cu-app .scaler-row {
grid-template-columns: 1fr;
}
#cu-app .scaler-ingredient-item {
grid-template-columns: 1fr 1fr auto;
}
}
</style>

<h2>Cooking Unit Converter</h2>

<div class="tabs">
<button class="tab-btn active" onclick="cuShowTab('volume')">Volume</button>
<button class="tab-btn" onclick="cuShowTab('weight')">Weight</button>
<button class="tab-btn" onclick="cuShowTab('ingredient')">By Ingredient</button>
<button class="tab-btn" onclick="cuShowTab('scaler')">Recipe Scaler</button>
<button class="tab-btn" onclick="cuShowTab('reference')">Quick Reference</button>
</div>

<!-- VOLUME TAB -->
<div id="cu-tab-volume" class="panel active">
<div class="converter-grid">
<div>
<label>Amount</label>
<input type="number" id="vol-amount" value="1" min="0" step="any" oninput="cuConvertVolume()">
</div>
<div style="display:flex;align-items:flex-end;padding-bottom:0.2rem;">
<button class="swap-btn" onclick="cuSwapVolume()" title="Swap units">&#8644;</button>
</div>
<div>
<label>Result</label>
<input type="number" id="vol-result" value="" min="0" step="any" oninput="cuConvertVolumeReverse()">
</div>
</div>
<div style="display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin-bottom:1rem;">
<div>
<label>From Unit</label>
<select id="vol-from" onchange="cuConvertVolume()">
<option value="cup">Cup (US)</option>
<option value="tbsp">Tablespoon (tbsp)</option>
<option value="tsp">Teaspoon (tsp)</option>
<option value="ml">Milliliter (ml)</option>
<option value="liter">Liter (L)</option>
<option value="floz">Fluid Ounce (fl oz)</option>
</select>
</div>
<div>
<label>To Unit</label>
<select id="vol-to" onchange="cuConvertVolume()">
<option value="cup">Cup (US)</option>
<option value="tbsp">Tablespoon (tbsp)</option>
<option value="tsp">Teaspoon (tsp)</option>
<option value="ml" selected>Milliliter (ml)</option>
<option value="liter">Liter (L)</option>
<option value="floz">Fluid Ounce (fl oz)</option>
</select>
</div>
</div>
<div class="result-box" id="vol-result-box">
<div class="result-value" id="vol-result-display">236.59 ml</div>
<div class="result-label">1 Cup (US) = 236.59 Milliliter (ml)</div>
</div>
<div class="tip-box">
Tip: 1 US Cup = 16 tablespoons = 48 teaspoons = 236.59 ml = 8 fl oz
</div>
</div>

<!-- WEIGHT TAB -->
<div id="cu-tab-weight" class="panel">
<div class="converter-grid">
<div>
<label>Amount</label>
<input type="number" id="wt-amount" value="1" min="0" step="any" oninput="cuConvertWeight()">
</div>
<div style="display:flex;align-items:flex-end;padding-bottom:0.2rem;">
<button class="swap-btn" onclick="cuSwapWeight()" title="Swap units">&#8644;</button>
</div>
<div>
<label>Result</label>
<input type="number" id="wt-result" value="" min="0" step="any" oninput="cuConvertWeightReverse()">
</div>
</div>
<div style="display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin-bottom:1rem;">
<div>
<label>From Unit</label>
<select id="wt-from" onchange="cuConvertWeight()">
<option value="g">Gram (g)</option>
<option value="kg">Kilogram (kg)</option>
<option value="oz">Ounce (oz)</option>
<option value="lb">Pound (lb)</option>
</select>
</div>
<div>
<label>To Unit</label>
<select id="wt-to" onchange="cuConvertWeight()">
<option value="g">Gram (g)</option>
<option value="kg">Kilogram (kg)</option>
<option value="oz" selected>Ounce (oz)</option>
<option value="lb">Pound (lb)</option>
</select>
</div>
</div>
<div class="result-box" id="wt-result-box">
<div class="result-value" id="wt-result-display">0.04 oz</div>
<div class="result-label">1 Gram (g) = 0.04 Ounce (oz)</div>
</div>
<div class="tip-box">
Tip: 1 oz = 28.35 g &nbsp;|&nbsp; 1 lb = 16 oz = 453.59 g &nbsp;|&nbsp; 1 kg = 2.205 lb
</div>
</div>

<!-- INGREDIENT TAB -->
<div id="cu-tab-ingredient" class="panel">
<p style="font-size:0.9rem;color:#555;margin-top:0;">Convert volume to weight (or vice versa) using ingredient density.</p>
<div class="ingredient-row">
<div>
<label>Ingredient</label>
<select id="ing-type" onchange="cuConvertIngredient()">
<option value="water">Water</option>
<option value="milk">Milk (whole)</option>
<option value="flour">All-Purpose Flour</option>
<option value="sugar_white">White Sugar (granulated)</option>
<option value="sugar_brown">Brown Sugar (packed)</option>
<option value="sugar_powder">Powdered Sugar</option>
<option value="butter">Butter</option>
<option value="oil">Vegetable Oil</option>
<option value="honey">Honey</option>
<option value="rice">Rice (uncooked)</option>
<option value="oats">Oats (rolled)</option>
<option value="cocoa">Cocoa Powder</option>
<option value="salt">Table Salt</option>
<option value="baking_powder">Baking Powder</option>
</select>
</div>
<div>
<label>Amount</label>
<input type="number" id="ing-amount" value="1" min="0" step="any" oninput="cuConvertIngredient()">
</div>
<div>
<label>From Unit</label>
<select id="ing-from" onchange="cuConvertIngredient()">
<option value="cup">Cup</option>
<option value="tbsp">Tablespoon</option>
<option value="tsp">Teaspoon</option>
<option value="ml">ml</option>
<option value="floz">fl oz</option>
<option value="g">Gram</option>
<option value="oz">Ounce</option>
</select>
</div>
</div>
<div class="result-box" id="ing-result-box">
<div class="result-value" id="ing-result-display">--</div>
<div class="result-label" id="ing-result-label">Select an ingredient and amount</div>
</div>
<div id="ing-all-conversions" style="margin-top:1rem;"></div>
</div>

<!-- RECIPE SCALER TAB -->
<div id="cu-tab-scaler" class="panel">
<p style="font-size:0.9rem;color:#555;margin-top:0;">Scale any recipe up or down by entering your ingredients below.</p>
<div class="scaler-row">
<div>
<label>Original Servings</label>
<input type="number" id="sc-original" value="4" min="0.1" step="any">
</div>
<div>
<label>Desired Servings</label>
<input type="number" id="sc-desired" value="6" min="0.1" step="any">
</div>
</div>
<div class="scaler-ingredients" id="sc-ingredients">
<label style="margin-bottom:0.5rem;display:block;">Ingredients</label>
<div class="scaler-ingredient-item" id="sc-row-0">
<input type="number" placeholder="Amount" value="2" min="0" step="any">
<select>
<option value="cup">Cup</option>
<option value="tbsp">Tablespoon</option>
<option value="tsp">Teaspoon</option>
<option value="ml">ml</option>
<option value="g">gram</option>
<option value="oz">oz</option>
<option value="lb">lb</option>
<option value="piece">piece(s)</option>
</select>
<button class="remove-btn" onclick="cuRemoveRow(this)">&#10005;</button>
</div>
<div class="scaler-ingredient-item" id="sc-row-1">
<input type="number" placeholder="Amount" value="1" min="0" step="any">
<select>
<option value="cup">Cup</option>
<option value="tbsp" selected>Tablespoon</option>
<option value="tsp">Teaspoon</option>
<option value="ml">ml</option>
<option value="g">gram</option>
<option value="oz">oz</option>
<option value="lb">lb</option>
<option value="piece">piece(s)</option>
</select>
<button class="remove-btn" onclick="cuRemoveRow(this)">&#10005;</button>
</div>
</div>
<div style="margin-top:0.8rem;">
<button class="add-btn" onclick="cuAddRow()">+ Add Ingredient</button>
<button class="calc-btn" onclick="cuScaleRecipe()">Scale Recipe</button>
</div>
<div class="scaler-result" id="sc-result" style="display:none;">
<table>
<thead>
<tr>
<th>Original</th>
<th>Scaled Amount</th>
</tr>
</thead>
<tbody id="sc-result-body"></tbody>
</table>
<div style="font-size:0.82rem;color:#888;margin-top:0.6rem;" id="sc-factor-label"></div>
</div>
</div>

<!-- QUICK REFERENCE TAB -->
<div id="cu-tab-reference" class="panel">
<h2>Volume Quick Reference</h2>
<table class="ref-table">
<thead>
<tr>
<th>Measurement</th>
<th>Cups</th>
<th>Tbsp</th>
<th>Tsp</th>
<th>ml</th>
<th>fl oz</th>
</tr>
</thead>
<tbody>
<tr><td><strong>1 Cup</strong></td><td>1</td><td>16</td><td>48</td><td>236.6</td><td>8</td></tr>
<tr><td><strong>3/4 Cup</strong></td><td>0.75</td><td>12</td><td>36</td><td>177.4</td><td>6</td></tr>
<tr><td><strong>2/3 Cup</strong></td><td>0.667</td><td>10.67</td><td>32</td><td>157.7</td><td>5.33</td></tr>
<tr><td><strong>1/2 Cup</strong></td><td>0.5</td><td>8</td><td>24</td><td>118.3</td><td>4</td></tr>
<tr><td><strong>1/3 Cup</strong></td><td>0.333</td><td>5.33</td><td>16</td><td>78.9</td><td>2.67</td></tr>
<tr><td><strong>1/4 Cup</strong></td><td>0.25</td><td>4</td><td>12</td><td>59.1</td><td>2</td></tr>
<tr><td><strong>1 Tbsp</strong></td><td>0.0625</td><td>1</td><td>3</td><td>14.79</td><td>0.5</td></tr>
<tr><td><strong>1 Tsp</strong></td><td>0.0208</td><td>0.333</td><td>1</td><td>4.93</td><td>0.167</td></tr>
<tr><td><strong>1 fl oz</strong></td><td>0.125</td><td>2</td><td>6</td><td>29.57</td><td>1</td></tr>
<tr><td><strong>1 Liter</strong></td><td>4.227</td><td>67.63</td><td>202.9</td><td>1000</td><td>33.81</td></tr>
</tbody>
</table>

<h2>Common Ingredient Weights (per 1 Cup)</h2>
<table class="ref-table">
<thead>
<tr>
<th>Ingredient</th>
<th>Grams</th>
<th>Ounces</th>
</tr>
</thead>
<tbody>
<tr><td>All-Purpose Flour</td><td>125 g</td><td>4.4 oz</td></tr>
<tr><td>White Sugar (granulated)</td><td>200 g</td><td>7.1 oz</td></tr>
<tr><td>Brown Sugar (packed)</td><td>220 g</td><td>7.8 oz</td></tr>
<tr><td>Powdered Sugar</td><td>120 g</td><td>4.2 oz</td></tr>
<tr><td>Butter</td><td>227 g</td><td>8.0 oz</td></tr>
<tr><td>Vegetable Oil</td><td>218 g</td><td>7.7 oz</td></tr>
<tr><td>Milk (whole)</td><td>244 g</td><td>8.6 oz</td></tr>
<tr><td>Water</td><td>237 g</td><td>8.4 oz</td></tr>
<tr><td>Honey</td><td>340 g</td><td>12.0 oz</td></tr>
<tr><td>Rice (uncooked)</td><td>185 g</td><td>6.5 oz</td></tr>
<tr><td>Rolled Oats</td><td>90 g</td><td>3.2 oz</td></tr>
<tr><td>Cocoa Powder</td><td>85 g</td><td>3.0 oz</td></tr>
</tbody>
</table>

<h2>Weight Quick Reference</h2>
<table class="ref-table">
<thead>
<tr>
<th>From</th>
<th>Grams</th>
<th>Kilograms</th>
<th>Ounces</th>
<th>Pounds</th>
</tr>
</thead>
<tbody>
<tr><td><strong>1 gram</strong></td><td>1</td><td>0.001</td><td>0.035</td><td>0.0022</td></tr>
<tr><td><strong>1 kilogram</strong></td><td>1000</td><td>1</td><td>35.27</td><td>2.205</td></tr>
<tr><td><strong>1 ounce</strong></td><td>28.35</td><td>0.028</td><td>1</td><td>0.0625</td></tr>
<tr><td><strong>1 pound</strong></td><td>453.6</td><td>0.454</td><td>16</td><td>1</td></tr>
</tbody>
</table>
</div>

<div class="related-tools">
<h3>Related Free Tools</h3>
<ul>
<li><a href="/tools/bmi-calculator/">BMI Calculator</a> — Body Mass Index calculator for adults</li>
<li><a href="/tools/calorie-calculator/">Calorie Calculator</a> — Daily calorie needs estimator</li>
<li><a href="/tools/tip-calculator/">Tip Calculator</a> — Split bills and calculate tips easily</li>
<li><a href="/tools/unit-converter/">Unit Converter</a> — Length, area, temperature, and more</li>
</ul>
</div>

<script>
(function() {
// --- Volume conversion (base: ml) ---
var VOL_TO_ML = {
cup: 236.5882,
tbsp: 14.7868,
tsp: 4.9289,
ml: 1,
liter: 1000,
floz: 29.5735
};
var VOL_NAMES = {
cup: 'Cup (US)', tbsp: 'Tablespoon (tbsp)', tsp: 'Teaspoon (tsp)',
ml: 'Milliliter (ml)', liter: 'Liter (L)', floz: 'Fluid Ounce (fl oz)'
};

// --- Weight conversion (base: grams) ---
var WT_TO_G = { g: 1, kg: 1000, oz: 28.3495, lb: 453.592 };
var WT_NAMES = { g: 'Gram (g)', kg: 'Kilogram (kg)', oz: 'Ounce (oz)', lb: 'Pound (lb)' };

// --- Ingredient density: grams per ml ---
var ING_DENSITY = {
water: 1.0,
milk: 1.03,
flour: 0.529,
sugar_white: 0.845,
sugar_brown: 0.930,
sugar_powder: 0.507,
butter: 0.959,
oil: 0.920,
honey: 1.436,
rice: 0.782,
oats: 0.380,
cocoa: 0.359,
salt: 1.217,
baking_powder: 0.900
};
var ING_NAMES = {
water: 'Water', milk: 'Milk (whole)', flour: 'All-Purpose Flour',
sugar_white: 'White Sugar', sugar_brown: 'Brown Sugar (packed)',
sugar_powder: 'Powdered Sugar', butter: 'Butter', oil: 'Vegetable Oil',
honey: 'Honey', rice: 'Rice (uncooked)', oats: 'Rolled Oats',
cocoa: 'Cocoa Powder', salt: 'Table Salt', baking_powder: 'Baking Powder'
};

function cuFmt(n) {
if (n === null || isNaN(n)) return '--';
if (Math.abs(n) >= 1000) return parseFloat(n.toFixed(2)).toLocaleString();
if (Math.abs(n) >= 10) return parseFloat(n.toFixed(3)).toString();
if (Math.abs(n) >= 0.01) return parseFloat(n.toFixed(4)).toString();
return parseFloat(n.toFixed(6)).toString();
}

window.cuShowTab = function(tab) {
document.querySelectorAll('#cu-app .panel').forEach(function(p) { p.classList.remove('active'); });
document.querySelectorAll('#cu-app .tab-btn').forEach(function(b) { b.classList.remove('active'); });
document.getElementById('cu-tab-' + tab).classList.add('active');
event.target.classList.add('active');
};

// Volume
window.cuConvertVolume = function() {
var amt = parseFloat(document.getElementById('vol-amount').value);
var from = document.getElementById('vol-from').value;
var to = document.getElementById('vol-to').value;
if (isNaN(amt)) return;
var ml = amt * VOL_TO_ML[from];
var res = ml / VOL_TO_ML[to];
document.getElementById('vol-result').value = cuFmt(res);
document.getElementById('vol-result-display').textContent = cuFmt(res) + ' ' + VOL_NAMES[to];
document.querySelector('#vol-result-box .result-label').textContent =
cuFmt(amt) + ' ' + VOL_NAMES[from] + ' = ' + cuFmt(res) + ' ' + VOL_NAMES[to];
};
window.cuConvertVolumeReverse = function() {
var amt = parseFloat(document.getElementById('vol-result').value);
var from = document.getElementById('vol-from').value;
var to = document.getElementById('vol-to').value;
if (isNaN(amt)) return;
var ml = amt * VOL_TO_ML[to];
var res = ml / VOL_TO_ML[from];
document.getElementById('vol-amount').value = cuFmt(res);
document.getElementById('vol-result-display').textContent = cuFmt(amt) + ' ' + VOL_NAMES[to];
document.querySelector('#vol-result-box .result-label').textContent =
cuFmt(res) + ' ' + VOL_NAMES[from] + ' = ' + cuFmt(amt) + ' ' + VOL_NAMES[to];
};
window.cuSwapVolume = function() {
var f = document.getElementById('vol-from');
var t = document.getElementById('vol-to');
var tmp = f.value; f.value = t.value; t.value = tmp;
cuConvertVolume();
};

// Weight
window.cuConvertWeight = function() {
var amt = parseFloat(document.getElementById('wt-amount').value);
var from = document.getElementById('wt-from').value;
var to = document.getElementById('wt-to').value;
if (isNaN(amt)) return;
var g = amt * WT_TO_G[from];
var res = g / WT_TO_G[to];
document.getElementById('wt-result').value = cuFmt(res);
document.getElementById('wt-result-display').textContent = cuFmt(res) + ' ' + WT_NAMES[to];
document.querySelector('#wt-result-box .result-label').textContent =
cuFmt(amt) + ' ' + WT_NAMES[from] + ' = ' + cuFmt(res) + ' ' + WT_NAMES[to];
};
window.cuConvertWeightReverse = function() {
var amt = parseFloat(document.getElementById('wt-result').value);
var from = document.getElementById('wt-from').value;
var to = document.getElementById('wt-to').value;
if (isNaN(amt)) return;
var g = amt * WT_TO_G[to];
var res = g / WT_TO_G[from];
document.getElementById('wt-amount').value = cuFmt(res);
document.getElementById('wt-result-display').textContent = cuFmt(amt) + ' ' + WT_NAMES[to];
document.querySelector('#wt-result-box .result-label').textContent =
cuFmt(res) + ' ' + WT_NAMES[from] + ' = ' + cuFmt(amt) + ' ' + WT_NAMES[to];
};
window.cuSwapWeight = function() {
var f = document.getElementById('wt-from');
var t = document.getElementById('wt-to');
var tmp = f.value; f.value = t.value; t.value = tmp;
cuConvertWeight();
};

// Ingredient converter
window.cuConvertIngredient = function() {
var ing = document.getElementById('ing-type').value;
var amt = parseFloat(document.getElementById('ing-amount').value);
var from = document.getElementById('ing-from').value;
if (isNaN(amt)) return;
var density = ING_DENSITY[ing]; // g/ml
// convert amt to grams
var grams;
var isVol = ['cup','tbsp','tsp','ml','floz'].indexOf(from) >= 0;
if (isVol) {
var ml = amt * VOL_TO_ML[from === 'floz' ? 'floz' : from];
grams = ml * density;
} else if (from === 'g') {
grams = amt;
} else { // oz
grams = amt * 28.3495;
}
var ml_val = grams / density;
// Build all conversions
var res = document.getElementById('ing-result-display');
var lbl = document.getElementById('ing-result-label');
var ingName = ING_NAMES[ing];
if (isVol) {
res.textContent = cuFmt(grams) + ' g  /  ' + cuFmt(grams/28.3495) + ' oz';
lbl.textContent = cuFmt(amt) + ' ' + from + ' of ' + ingName;
} else {
res.textContent = cuFmt(ml_val) + ' ml  /  ' + cuFmt(ml_val/VOL_TO_ML['cup']) + ' cups';
lbl.textContent = cuFmt(grams) + ' g of ' + ingName;
}
// All conversions table
var html = '<table class="ref-table" style="font-size:0.85rem;"><thead><tr><th>Unit</th><th>Amount</th></tr></thead><tbody>';
html += '<tr><td>Grams</td><td>' + cuFmt(grams) + ' g</td></tr>';
html += '<tr><td>Ounces</td><td>' + cuFmt(grams/28.3495) + ' oz</td></tr>';
html += '<tr><td>Cups</td><td>' + cuFmt(ml_val/VOL_TO_ML['cup']) + ' cup</td></tr>';
html += '<tr><td>Tablespoons</td><td>' + cuFmt(ml_val/VOL_TO_ML['tbsp']) + ' tbsp</td></tr>';
html += '<tr><td>Teaspoons</td><td>' + cuFmt(ml_val/VOL_TO_ML['tsp']) + ' tsp</td></tr>';
html += '<tr><td>Milliliters</td><td>' + cuFmt(ml_val) + ' ml</td></tr>';
html += '<tr><td>Fluid Ounces</td><td>' + cuFmt(ml_val/VOL_TO_ML['floz']) + ' fl oz</td></tr>';
html += '</tbody></table>';
document.getElementById('ing-all-conversions').innerHTML = html;
};

// Recipe Scaler
var cuRowCount = 2;
window.cuAddRow = function() {
var container = document.getElementById('sc-ingredients');
var div = document.createElement('div');
div.className = 'scaler-ingredient-item';
div.id = 'sc-row-' + cuRowCount;
div.innerHTML = '<input type="number" placeholder="Amount" value="1" min="0" step="any">' +
'<select>' +
'<option value="cup">Cup</option>' +
'<option value="tbsp">Tablespoon</option>' +
'<option value="tsp">Teaspoon</option>' +
'<option value="ml">ml</option>' +
'<option value="g">gram</option>' +
'<option value="oz">oz</option>' +
'<option value="lb">lb</option>' +
'<option value="piece">piece(s)</option>' +
'</select>' +
'<button class="remove-btn" onclick="cuRemoveRow(this)">&#10005;</button>';
container.appendChild(div);
cuRowCount++;
};
window.cuRemoveRow = function(btn) {
btn.parentElement.remove();
};
window.cuScaleRecipe = function() {
var orig = parseFloat(document.getElementById('sc-original').value);
var desired = parseFloat(document.getElementById('sc-desired').value);
if (isNaN(orig) || isNaN(desired) || orig <= 0 || desired <= 0) return;
var factor = desired / orig;
var rows = document.querySelectorAll('#sc-ingredients .scaler-ingredient-item');
var tbody = document.getElementById('sc-result-body');
tbody.innerHTML = '';
rows.forEach(function(row) {
var amt = parseFloat(row.querySelector('input').value);
var unit = row.querySelector('select').value;
if (isNaN(amt)) return;
var scaled = amt * factor;
var tr = document.createElement('tr');
tr.innerHTML = '<td>' + cuFmt(amt) + ' ' + unit + '</td><td><strong>' + cuFmt(scaled) + ' ' + unit + '</strong></td>';
tbody.appendChild(tr);
});
document.getElementById('sc-factor-label').textContent =
'Scale factor: x' + cuFmt(factor) + '  (' + orig + ' servings → ' + desired + ' servings)';
document.getElementById('sc-result').style.display = 'block';
};

// Init defaults
cuConvertVolume();
cuConvertWeight();
cuConvertIngredient();
})();
</script>

</div>

---

## Related Tools

> [Carbon Footprint Calculator](/tools/carbon-footprint-calculator/)
> [Electricity Cost Calculator](/tools/electricity-cost-calculator/)
> [Fuel Cost Calculator](/tools/fuel-cost-calculator/)

