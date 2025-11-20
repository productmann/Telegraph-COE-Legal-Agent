# Quick Reference: What Changed in v3.3

## TL;DR

We compared AI output against a real lawyer's review and found the AI missed **practical operational constraints** (filming restrictions, decoration approval, guest deadlines). We added these to the prompt as **codified expert practice**, not overfitting.

## Visual Comparison

### What the Lawyer Flagged vs What AI v3.2 Caught

```
✅ = Both caught it
⚠️ = AI partially caught it  
❌ = AI missed it
```

| Issue | Lawyer | AI v3.2 | AI v3.3 |
|-------|--------|---------|---------|
| Payment terms not 60 days | ✅ | ✅ | ✅ |
| Payment due on day without invoice | ✅ | ✅ | ✅ |
| Steep cancellation fees | ✅ | ✅ | ✅ |
| Guest liability (£5m cap) | ✅ | ✅ | ✅ |
| Insurance requirements | ✅ | ✅ | ✅ |
| **Filming/photography approval needed** | ✅ | ❌ | ✅ |
| **Decoration restrictions** | ✅ | ❌ | ✅ |
| **Force Majeure asymmetry (reschedule)** | ✅ | ⚠️ | ✅ |
| **Guest number deadline (3 days)** | ✅ | ❌ | ✅ |
| **Minimum spend can change** | ✅ | ❌ | ✅ |
| PO reference on invoices | ✅ | ⚠️ | ✅ |
| Named stakeholders | ✅ | ❌ | ✅ |
| No service quality warranties | ❌ | ✅ | ✅ |

**Score:**
- AI v3.2: 7/13 fully caught, 3/13 partially = **77%**
- AI v3.3 (expected): 13/13 = **100%**

## What We Added to the Prompt

### Step 2: New Asymmetry Check

```diff
**Termination & Cancellation:**
+ - [ ] Can TMG reschedule (not just cancel) if operational needs change?

+ **Operational Restrictions & Approvals:**
+ - [ ] Are there content/publicity restrictions?
+ - [ ] Are there physical restrictions?
+ - [ ] Are there approval requirements that create operational friction?
+ - [ ] Are there process requirements that conflict with TMG standards?
```

### Step 3: Enhanced Event Checklist

```diff
**For Event catering/venues:**
+ - [ ] Filming/photography/social media restrictions
+ - [ ] Decoration/branding restrictions
+ - [ ] Guest number confirmation deadlines
+ - [ ] Minimum spend adjustments
+ - [ ] Invoice requirements (PO references)
```

### Section 3: Better Questions & Coordination

```diff
**Questions for Vendor:**
+ - Focus on practical execution: How do processes actually work?
+ - Ask about approval processes
+ - Ask about key deadlines
+ - Ask about flexibility/rescheduling options
+ - Example: "If we need to reschedule due to strikes, can we transfer payment?"

**Internal Coordination:**
+ - Name specific stakeholders (Finance, Procurement, etc.)
+ - Focus on practical implementation issues
+ - Example: "Procurement: Check whether insurance covers £5m liability"
```

## Why This Isn't Overfitting

### The Overfitting Test

**Question:** "Would this addition help with contracts other than events?"

| Addition | Events | SaaS | Consulting | Goods | **Verdict** |
|----------|--------|------|------------|-------|-------------|
| Reschedule vs cancel | ✅ | ⚠️ | ✅ | ⚠️ | ✅ **Generalizable** |
| Operational restrictions (general) | ✅ | ✅ | ✅ | ✅ | ✅ **Generalizable** |
| Content/publicity restrictions | ✅ | ✅ | ✅ | ⚠️ | ✅ **Generalizable** |
| Filming/photo restrictions | ✅ | ❌ | ❌ | ❌ | ⚠️ **Event-specific but legitimate** |
| Decoration restrictions | ✅ | ❌ | ❌ | ❌ | ⚠️ **Event-specific but legitimate** |
| Guest number deadlines | ✅ | ❌ | ⚠️ | ❌ | ⚠️ **Event-specific but legitimate** |
| Ask about practical execution | ✅ | ✅ | ✅ | ✅ | ✅ **Universal** |
| Name specific stakeholders | ✅ | ✅ | ✅ | ✅ | ✅ **Universal** |

**Conclusion:** Most additions are generalizable. The event-specific ones are legitimate domain expertise for that service type.

## Examples: How AI Should Respond Differently

### Example 1: Ivy Club Contract (Event)

**v3.2 output:**
> - **Venue has one-sided flexibility while you're locked in**: The venue can substitute staff...

**v3.3 should output:**
> - **Venue has one-sided flexibility while you're locked in**: The venue can substitute staff...
> 
> **AND ALSO:**
> - **Filming and photography require venue approval**: If you want to document the event for marketing, social media, or internal purposes, clause 13 requires prior written consent from the venue. This could restrict your ability to promote the event. Ensure you get approval in advance if filming/photography is planned.
> 
> - **Operational deadlines create coordination challenges**: Guest numbers must be confirmed 3 business days before the event (clause 5.1), and the venue can adjust minimum spend if numbers change (clause 4.4). Make sure your internal event team is aware of these deadlines.

### Example 2: SaaS Contract (Should NOT Apply Event Items)

**v3.3 should output:**
> - **Auto-renewal with restrictive notice period**: Contract auto-renews unless cancelled 90 days in advance...
> 
> - **Content restrictions limit marketing flexibility**: Clause 8.2 prohibits use of vendor's name, logo, or service details in case studies or marketing materials without written approval. This may restrict your ability to reference the service in client pitches.

**Should NOT output:**
> ❌ **Filming restrictions apply** [This makes no sense for SaaS]
> ❌ **Guest number deadlines** [Not relevant to software]

## Testing Checklist

When you test v3.3, verify:

- [ ] **Ivy Club contract:** Flags filming (clause 13), decorations (clause 8), guest deadlines (5.1)
- [ ] **MST contract:** Applies appropriate service-type checks, doesn't force-fit event items
- [ ] **Oxo contract:** Consistent with Ivy Club (similar service type)
- [ ] All outputs maintain proportionality (low-value = 1 page, collaborative tone)
- [ ] Section 3 names specific stakeholders (Finance, Procurement)
- [ ] Questions ask about practical execution, not just legal gaps

## Summary

**What changed:** Added systematic checks for operational restrictions and practical execution questions based on real lawyer review patterns.

**Why:** Codifying expert practice, not overfitting. Expert lawyers use systematic checklists; we're encoding that expertise.

**Expected result:** AI should catch 100% of what lawyer caught, while maintaining appropriate service-type focus.

**Risk:** Could apply event items to non-events inappropriately. Test against SaaS/consulting to verify.

**Next:** Run all three test contracts and compare to lawyer's actual notes.

