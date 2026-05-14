---
title: "Budget Planner | Free Monthly Budget Calculator"
date: 2026-05-14
draft: false
slug: "budget-planner"
description: "Free budget planner calculator. Enter your monthly income to get a recommended spending breakdown based on the 50/30/20 rule. Start budgeting in seconds."
author: "Productivity Works Editorial"
categories:
  - "Investing & Finance"
tags:
  - "budget"
  - "calculator"
  - "personal finance"
  - "savings"
  - "tools"
ShowReadingTime: false
ShowWordCount: false
ShowToc: false
TocOpen: false
ShowBreadCrumbs: true
cover:
  image: "/images/covers/budget-planner.png"
  alt: "Budget Planner | Free Monthly Budget Calculator"
  relative: false
---

*This page contains affiliate links.*

# Budget Planner | 50/30/20 Rule Calculator

Enter your monthly take-home pay to get a **recommended spending breakdown** based on the 50/30/20 budgeting rule.

<div id="budget-calc" style="max-width:640px;margin:0 auto;padding:24px;border:2px solid #2563eb;border-radius:12px;background:#f8fafc;">

<div style="margin-bottom:24px;">
<label style="display:block;font-weight:bold;margin-bottom:6px;">Monthly Take-Home Pay ($)</label>
<input type="range" id="monthlyPay" min="1000" max="15000" step="100" value="5000" oninput="calcBudget()" style="width:100%;">
<div style="display:flex;justify-content:space-between;font-size:13px;color:#64748b;"><span>$1,000</span><span id="payVal" style="font-weight:bold;font-size:18px;color:#2563eb;">$5,000</span><span>$15,000</span></div>
</div>

<div style="background:#1e40af;color:white;border-radius:8px;padding:20px;text-align:center;margin-bottom:16px;">
<div style="font-size:14px;margin-bottom:4px;">Monthly Savings Target (20%)</div>
<div id="savingsAmt" style="font-size:36px;font-weight:bold;">$1,000</div>
<div style="font-size:13px;margin-top:4px;">Annual savings: <span id="savingsYearly" style="font-weight:bold;">$12,000</span></div>
</div>

<div style="margin-bottom:16px;">

<div style="display:flex;align-items:center;padding:12px 0;border-bottom:1px solid #e2e8f0;">
<div style="width:16px;height:16px;border-radius:50%;background:#ef4444;margin-right:12px;flex-shrink:0;"></div>
<div style="flex:1;"><strong>Needs (50%)</strong><br><span style="font-size:13px;color:#64748b;">Housing, food, utilities, insurance, transport</span></div>
<div style="font-weight:bold;font-size:18px;" id="needsAmt">$2,500</div>
</div>

<div style="display:flex;align-items:center;padding:12px 0;border-bottom:1px solid #e2e8f0;">
<div style="width:16px;height:16px;border-radius:50%;background:#f59e0b;margin-right:12px;flex-shrink:0;"></div>
<div style="flex:1;"><strong>Wants (30%)</strong><br><span style="font-size:13px;color:#64748b;">Dining out, entertainment, shopping, hobbies</span></div>
<div style="font-weight:bold;font-size:18px;" id="wantsAmt">$1,500</div>
</div>

<div style="display:flex;align-items:center;padding:12px 0;border-bottom:1px solid #e2e8f0;">
<div style="width:16px;height:16px;border-radius:50%;background:#2563eb;margin-right:12px;flex-shrink:0;"></div>
<div style="flex:1;"><strong>Savings & Debt (20%)</strong><br><span style="font-size:13px;color:#64748b;">Emergency fund, investments, debt repayment</span></div>
<div style="font-weight:bold;font-size:18px;" id="saveAmt">$1,000</div>
</div>

</div>

<div style="background:#dcfce7;border-radius:8px;padding:16px;margin-bottom:16px;">
<div style="font-size:13px;color:#15803d;margin-bottom:4px;"><strong>If you invest your 20% savings:</strong></div>
<div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;">
<div style="text-align:center;"><div style="font-size:12px;color:#64748b;">In 10 years (7% return)</div><div id="invest10" style="font-weight:bold;color:#15803d;font-size:16px;">$173,085</div></div>
<div style="text-align:center;"><div style="font-size:12px;color:#64748b;">In 30 years (7% return)</div><div id="invest30" style="font-weight:bold;color:#15803d;font-size:16px;">$1,219,971</div></div>
</div>
</div>

<div style="background:#f1f5f9;border-radius:8px;padding:12px;font-size:13px;color:#475569;">
<strong>The 50/30/20 Rule:</strong> Popularized by Senator Elizabeth Warren, this simple framework allocates 50% of after-tax income to needs, 30% to wants, and 20% to savings/debt repayment.
</div>

</div>

<script>
function calcBudget(){
  var pay=parseInt(document.getElementById('monthlyPay').value);
  var needs=Math.floor(pay*0.5);
  var wants=Math.floor(pay*0.3);
  var save=Math.floor(pay*0.2);

  // Investment projections at 7% annual return
  var mr=0.07/12;
  var fv10=save*((Math.pow(1+mr,120)-1)/mr);
  var fv30=save*((Math.pow(1+mr,360)-1)/mr);

  document.getElementById('payVal').textContent='$'+pay.toLocaleString();
  document.getElementById('savingsAmt').textContent='$'+save.toLocaleString();
  document.getElementById('savingsYearly').textContent='$'+(save*12).toLocaleString();
  document.getElementById('needsAmt').textContent='$'+needs.toLocaleString();
  document.getElementById('wantsAmt').textContent='$'+wants.toLocaleString();
  document.getElementById('saveAmt').textContent='$'+save.toLocaleString();
  document.getElementById('invest10').textContent='$'+Math.floor(fv10).toLocaleString();
  document.getElementById('invest30').textContent='$'+Math.floor(fv30).toLocaleString();
}
calcBudget();
</script>

---

## How To Use Your Budget

### Needs (50%) Breakdown
| Category | Typical % of Income |
|----------|-------------------|
| Housing (rent/mortgage) | 25-30% |
| Groceries | 10-15% |
| Utilities | 3-5% |
| Transportation | 5-10% |
| Insurance | 3-5% |

### Where To Put Your 20% Savings
1. **Emergency fund first** — 3-6 months of expenses in a high-yield savings account
2. **Max out employer 401(k) match** — Free money, don't leave it on the table
3. **Invest the rest** — Low-cost index funds through a brokerage account

Use our [Compound Interest Calculator](/tools/compound-interest-calculator/) to see how your savings grow over time.

---

## FAQ

**Q: What if I can't save 20%?**
Start with whatever you can — even 5% is better than nothing. Automate your savings and increase by 1% each month.

**Q: Should I include debt payments in the 20%?**
Yes. Minimum debt payments go under "Needs" (50%), but extra payments toward debt reduction count as part of your 20%.

**Q: What if my needs exceed 50%?**
This is common in high cost-of-living areas. Look for ways to reduce your biggest expense (usually housing) or increase income.

---

## Related Tools

- [Compound Interest Calculator](/tools/compound-interest-calculator/) — See your investment growth
- [Loan Repayment Calculator](/tools/loan-repayment-calculator/) — Plan your debt payoff
