# Changelog v3.3 - Codifying Expert Review Practice

**Date:** November 18, 2025  
**Focus:** Incorporating real lawyer review patterns into the AI agent

## Context

After comparing AI output against an actual lawyer's review (Melonie Philips' review of the Ivy Club contract), we identified gaps where the AI missed practical operational constraints that experienced lawyers immediately flag. Rather than viewing these additions as "overfitting," we recognize this as **codifying expert practice** - capturing the systematic heuristics that expert lawyers use across all contract types.

## Key Philosophy Shift

**Previous thinking:** "Are we overfitting to one contract type?"  
**Correct framing:** "Are we codifying domain expertise that applies systematically?"

Expert lawyers have internalized checklists for different contract types through experience. The service-type branching logic already exists in the prompt - we're just improving one branch based on observed expert behavior.

## Changes Made

### 1. Enhanced Step 2: Asymmetries Check

**Location:** STEP 2: IDENTIFY ASYMMETRIES FIRST

**Added to Termination & Cancellation:**
```markdown
- [ ] Can TMG reschedule (not just cancel) if operational needs change?
```

**Rationale:** The lawyer specifically flagged: "There is nothing re us moving the event if we want or need to...I'd ask them about this via email and get them to confirm if we need to move because of strike, we can and any monies paid will be transferred."

The distinction between "cancel with penalty" vs "reschedule with payment transfer" is a genuine business flexibility issue applicable across many service types (events, consulting, training, maintenance contracts).

**New Section Added: Operational Restrictions & Approvals**
```markdown
**Operational Restrictions & Approvals:**
- [ ] Are there content/publicity restrictions? (filming, photography, social media, press releases)
- [ ] Are there physical restrictions? (decorations, signage, branding, access to premises)
- [ ] Are there approval requirements that create operational friction or deadlines?
- [ ] Are there process requirements that conflict with TMG's standard practices? (PO references, invoice format, payment methods)
```

**Rationale:** These are general principles that apply across contract types:
- **SaaS contracts** often restrict publicity/case studies
- **Consulting contracts** may restrict use of deliverables in marketing
- **Physical goods** may restrict resale or modification
- **Event venues** restrict filming/decorations

This is a **generalizable pattern** - "check for operational restrictions" - not an event-specific checklist.

### 2. Enhanced Step 3: Event Catering Checklist

**Location:** STEP 3: IDENTIFY PRACTICAL COMMERCIAL ISSUES

**Added to Event catering/venues checklist:**
```markdown
- [ ] Filming/photography/social media restrictions - does TMG need approval to document the event?
- [ ] Decoration/branding restrictions - can TMG bring decorations, signage, or branded materials?
- [ ] Guest number confirmation deadlines - what's the cutoff for final numbers?
- [ ] Minimum spend adjustments - can venue change minimum spend if guest numbers change?
- [ ] Invoice requirements - will vendor provide proper VAT invoices with PO references?
```

**Rationale - Item by Item:**

| Addition | Lawyer Flagged? | Event-Specific? | Justification |
|----------|----------------|-----------------|---------------|
| Filming/photography restrictions | ✅ Yes | ⚠️ Somewhat | Applies to talent agreements, brand partnerships, any contract where imagery/IP matters |
| Decoration/branding restrictions | ✅ Yes | ⚠️ Somewhat | Applies to physical spaces, retail agreements, co-branding arrangements |
| Guest number deadlines | ✅ Yes | ✅ Event-specific | Legitimate operational deadline for per-person pricing models |
| Minimum spend adjustments | ✅ Yes | ⚠️ Somewhat | Applies to usage-based pricing, minimum commitments in SaaS, etc. |
| Invoice/PO requirements | ✅ Yes (implicit) | ❌ Universal | Already in Override Terms §2, but worth emphasizing in checklist |

**Assessment:** Most additions are either universal or applicable to multiple contract types. The truly event-specific items (guest number deadlines) are legitimate operational constraints for that service type.

### 3. Enhanced Section 3: Questions for Vendor

**Location:** Section 3: RECOMMENDED ACTIONS

**Expanded guidance:**
```markdown
- **Questions for Vendor** (2-4 specific questions):
  - Focus on practical execution: How do processes actually work in practice?
  - Ask about ambiguities, subcontracting, insurance coverage, invoicing practices
  - Ask about approval processes: filming/photography, decorations, changes to arrangements
  - Ask about key deadlines: final numbers, payment timing, cancellation notice periods
  - Ask about flexibility: rescheduling options if business needs change (strikes, emergencies)
  - Examples: "Will you provide VAT invoices with our PO reference for each payment?" or 
    "If we need to reschedule due to strikes or emergencies, can we move the event and transfer payment?"
```

**Rationale:** The lawyer's note demonstrated asking practical execution questions that aren't necessarily "gaps" but clarify how the contract works in practice. This is expert behavior worth codifying.

**Key addition:** The rescheduling question specifically addresses the Force Majeure asymmetry the lawyer identified.

### 4. Enhanced Internal Coordination Guidance

**Location:** Section 3: RECOMMENDED ACTIONS

**Expanded guidance:**
```markdown
- **Internal Coordination** (1-3 action items):
  - Identify what internal teams need to check or approve
  - Be specific about what needs checking and why
  - Name specific stakeholders when possible (Finance, Procurement, etc.)
  - Focus on practical implementation issues, not just legal compliance
  - Examples: "Finance: Confirm comfortable with payment schedule requiring deposit on booking without invoice" 
    or "Procurement: Check whether our insurance covers £5m public liability and if insurers need 
    advance event notification"
```

**Rationale:** The lawyer named specific stakeholders ("Pat in procurement") and was very specific about what they needed to confirm. This is a pattern worth encoding.

### 5. Updated Service-Type Risk Focus

**Location:** Service-Type Risk Focus section

**Updated Event catering practical flags:**
```markdown
- **Event catering/venues**: 
  - Food quality, no-shows, damage liability, cancellation fees
  - **Practical flags**: VAT treatment, payment timing, guest liability, over-consumption clauses, 
    deposit refundability, filming/photography restrictions, decoration approval requirements, 
    guest number deadlines, minimum spend adjustment clauses, invoice/PO requirements
```

**Rationale:** Keeps the practical flags list aligned with the expanded Step 3 checklist.

## What We Deliberately Did NOT Add

### Items Rejected as Too Specific:
None - all additions were deemed generalizable or legitimately service-specific.

### Why This Isn't Overfitting:

The "overfitting test" asks: "Would this help with other contract types?"

| Addition | Helps with Events? | Helps with SaaS? | Helps with Consulting? | Helps with Goods? |
|----------|-------------------|------------------|------------------------|-------------------|
| Reschedule vs cancel | ✅ | ⚠️ Sometimes | ✅ | ⚠️ Sometimes |
| Operational restrictions (general) | ✅ | ✅ | ✅ | ✅ |
| Content/publicity restrictions | ✅ | ✅ | ✅ | ⚠️ Sometimes |
| Process alignment with TMG standards | ✅ | ✅ | ✅ | ✅ |

Most additions pass the generalizability test.

## Expected Impact

### What Should Improve:
1. ✅ AI should now catch filming/photography restrictions (missed in v3.2)
2. ✅ AI should now catch decoration/branding approval requirements (missed in v3.2)
3. ✅ AI should now explicitly ask about rescheduling flexibility, not just cancellation
4. ✅ AI should generate more specific internal coordination items with named stakeholders
5. ✅ AI should ask more practical execution questions beyond legal gaps

### What Should Stay the Same:
1. Contract value proportionality
2. Scenario-based Section 1 structure
3. Asymmetries-first approach
4. Collaborative tone for low-value contracts
5. Section 2 decision tree

## Testing Recommendations

### Test Case 1: Re-run Ivy Club Contract
**Expected improvements:**
- Should flag filming/photography restrictions (clause 13)
- Should flag decoration restrictions (clause 8)
- Should mention guest number confirmation deadline (clause 5.1)
- Should ask vendor about rescheduling flexibility
- Should suggest checking with Finance by name

### Test Case 2: Run Against SaaS Contract
**Test for overfitting:**
- Should NOT apply event-specific checks inappropriately
- SHOULD apply operational restrictions checks (e.g., case study approval, logo usage)
- SHOULD ask about reschedule/termination flexibility
- Should maintain appropriate service-type focus

### Test Case 3: Run Against Consulting Agreement
**Test for generalizability:**
- SHOULD check for content/deliverable usage restrictions
- SHOULD check for reschedule vs terminate distinction
- SHOULD ask about practical execution (payment milestones, acceptance criteria)
- Should NOT force-fit event-specific items

## Comparison: v3.2 vs v3.3

| Aspect | v3.2 Behavior | v3.3 Behavior |
|--------|---------------|---------------|
| **Filming restrictions** | ❌ Missed | ✅ Should catch |
| **Decoration restrictions** | ❌ Missed | ✅ Should catch |
| **Reschedule flexibility** | ⚠️ Partial (mentioned asymmetry) | ✅ Should explicitly flag and ask |
| **Guest number deadlines** | ❌ Missed | ✅ Should flag |
| **PO/invoice requirements** | ✅ Caught (via Override Terms) | ✅ Should emphasize more |
| **Named stakeholders** | ⚠️ Generic | ✅ Should name specific teams |
| **Practical execution questions** | ⚠️ Some | ✅ More systematic |

## Conclusion

These changes represent **codifying expert practice**, not overfitting. We're capturing the systematic heuristics that experienced lawyers use:

1. **Check operational restrictions** - applies to all contract types
2. **Distinguish reschedule from cancel** - applies to most service contracts
3. **Ask practical execution questions** - universal good practice
4. **Name specific stakeholders** - improves actionability
5. **Service-specific checklists** - legitimate domain expertise

The goal remains: create a **robust generalist** that replicates expert judgment across all contract types by encoding the systematic patterns experts use.

## Version Summary

- **v3.0-3.1:** Introduced mandatory workflow and asymmetry-first approach
- **v3.2:** Refined proportionality and practical commercial focus
- **v3.3:** Codified expert review patterns based on real lawyer comparison

**Next:** Test v3.3 against all three test contracts (Ivy Club, MST, Oxo) to validate improvements.





