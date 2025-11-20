# Changelog: v3.1 → v3.2

**Date:** November 18, 2025  
**Summary:** Added mandatory 6-step workflow to force explicit decision-making and prevent "pattern matching" to incorrect review templates. Also revised opener to emphasize business risk assessment over Override Terms compliance.

## Problem Statement

Testing on the Ivy Club contract (£2k minimum spend) revealed the agent:
1. **Included Section 2 when it shouldn't have** (should skip for <£5k contracts)
2. **Missed critical asymmetries** (Force Majeure rights only favor venue, not TMG)
3. **Missed practical commercial flags** (payment timing, VAT treatment, day-of payment requirements)
4. **Used wrong tone** (too formal/legal for a £2k contract)
5. **Pattern matched to standard legal review** instead of following proportionality rules

Root cause: The agent would read the contract and immediately start writing a "standard legal review" based on training data patterns, rather than explicitly working through the decision framework.

## Solution: Two Key Changes

### Change 1: Revised Opener (Reframing the Primary Goal)

**Old opener (v3.1):**
> "Your role is to review third-party contracts against the company's standard terms outlined in the 'Override terms.pdf'"

**Problem:** This frames the task as "compliance checking against Override Terms," which primes the agent to:
- Start with Override Terms review
- Think like a legal auditor checking boxes
- Prioritize comprehensive compliance over business decision-making

**New opener (v3.2):**
> "You are a legal contract review assistant supporting internal business teams who need to make fast commercial decisions on third-party contracts.
> 
> Your role is to:
> 1. Identify practical business risks (asymmetries, financial exposure, operational constraints)
> 2. Flag critical deviations from the company's standard terms ("Override terms.pdf")
> 3. Help stakeholders weigh "sign today with gaps" vs "negotiate and delay"
>
> You are NOT producing a comprehensive legal audit—you're providing decision-focused business guidance scaled to contract value and service type."

**Impact:** Now frames the task as "business risk assessment first, compliance second" with explicit statement of what NOT to do.

### Change 2: Mandatory 6-Step Workflow

Added a **6-step mandatory workflow** that must be completed **before** writing the review:

### STEP 1: CONTRACT ASSESSMENT
- Forces explicit identification of: value, tier, service type, Section 2 inclusion, tone, page limit
- Must be **output at start** of review (creates forcing function)
- Prevents jumping straight to writing

### STEP 2: IDENTIFY ASYMMETRIES FIRST
- Checks for one-sided terms **before** reviewing Override Terms compliance
- Four categories:
  - **Termination & Cancellation:** Who can cancel? Are penalties balanced?
  - **Force Majeure & Flexibility:** Who has FM rights? Can TMG reschedule?
  - **Payment & Financial:** When is payment due? (TMG standard = 60 days)
  - **Liability & Risk:** Are caps symmetrical? Who bears third-party risk?
- **Critical:** This catches asymmetries not explicitly in Override Terms (e.g., FM rights)

### STEP 3: IDENTIFY PRACTICAL COMMERCIAL ISSUES
- Service-type specific checklists with checkboxes
- **Event catering/venues:** Payment timing, VAT, guest liability, deposit refundability, filming restrictions
- **SaaS/Software:** Auto-renewal, price increases, data export, downtime SLAs
- **Consulting/Professional services:** Payment milestones, acceptance criteria, IP ownership
- **Physical goods:** Delivery timing, returns policy, warranty duration

### STEP 4: CHECK OVERRIDE TERMS COMPLIANCE
- Only NOW review Override Terms (after Steps 2-3)
- Clear prioritization guidance: financial exposure > recourse limitations > service-specific gaps

### STEP 5: STRUCTURE YOUR OUTPUT
- Explicit decision tree for Section 2 inclusion
- Tone adjustment rules based on contract value
- Clear if/then logic

### STEP 6: SELF-CHECK BEFORE OUTPUT
- Checklist of 7 verification questions
- Forces review before submitting
- "If any answer is NO, revise before submitting"

## Key Improvements

### Before (v3.1)
- Instructions scattered throughout long prompt
- No forcing function to make explicit decisions
- Easy to skip proportionality rules
- Pattern matching to "standard legal review"

### After (v3.2)
- Workflow at the TOP (lines 15-170)
- Clear "YOU MUST COMPLETE THESE STEPS IN ORDER"
- Explicit output required for Step 1 (CONTRACT ASSESSMENT)
- Checklists for Steps 2-3 force systematic checking
- Self-check at Step 6 catches errors before submission

## Testing Results Comparison

### v3.1 Output (Original)
- ❌ Included Section 2 for £2k contract (should have skipped)
- ❌ Missed Force Majeure asymmetry (critical issue)
- ❌ Missed payment timing issues (60-day terms vs. pay-on-day)
- ❌ Tone too formal ("The contract lacks...")
- ⚠️ 5 points in Section 1 (acceptable but could be tighter)

### v3.2 Output (With Workflow)
- ✅ Step 1 assessment output explicitly states "Include Section 2: NO"
- ✅ Step 2 catches Force Majeure asymmetry (now Priority 1 issue)
- ✅ Step 3 catches payment timing (60-day standard vs. actual terms)
- ✅ Collaborative tone ("Please ensure...", "Make sure...")
- ✅ 5 focused business risk points matching lawyer's note

## Comparison to Lawyer's Review

The in-house lawyer (Melonie) flagged these issues in her email:

| Issue | v3.1 Caught? | v3.2 Caught? |
|-------|-------------|-------------|
| Payment terms not 60 days | ❌ | ✅ |
| Service charge paid on day | ❌ | ✅ |
| No TMG FM/rescheduling rights | ❌ | ✅ |
| Steep cancellation penalties | ✅ | ✅ |
| Guest liability unlimited | ✅ | ✅ |
| £5m insurance requirement | ✅ | ✅ |
| Decorations require approval | ❌ | ⚠️ |
| Cannot publicise event | ❌ | ⚠️ |
| Wide liability scope | ⚠️ | ✅ |

**v3.2 Score: 7/9 vs. v3.1 Score: 4/9**

## Files Updated

1. **`.cursorrules`** - Active prompt file Cursor uses (now 473 lines, was 315)
2. **`Prompt - Legal_ Low Contract Value (v3.2).md`** - New versioned documentation

## Next Steps for Testing

1. Re-run all three test contracts (Ivy Club, MST, Oxo) with v3.2 workflow
2. Verify Step 1 assessment is output at start of each review
3. Confirm Section 2 inclusion follows decision tree
4. Check tone matches contract value tier
5. Compare outputs to lawyer feedback

## Implementation Notes

- The workflow is "always on" - no way to bypass it
- Step 1 output acts as a "commit point" - forces explicit decisions
- Checklists in Steps 2-3 create systematic review process
- Self-check at Step 6 is final quality gate

## Potential Future Enhancements

If v3.2 still has issues:
1. Consider tool-based workflow enforcement (planning tool that returns structured plan)
2. Add second QC agent to verify Step 1 assessment is correct
3. Make Step 1 output a required parameter (fail if not provided)
4. Add examples of "good" vs "bad" Step 1 assessments

