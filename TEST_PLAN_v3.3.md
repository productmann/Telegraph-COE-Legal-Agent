# Test Plan for v3.3

## Objective

Validate that v3.3 improvements successfully replicate expert lawyer review patterns without overfitting to event contracts.

## Test Contracts

1. **Ivy Club** (Event catering - £2,300) - Should show major improvements
2. **MST** (Training/Consulting) - Should not overfit to events
3. **Oxo** (Event catering) - Should be consistent with Ivy Club

## Test 1: Ivy Club Contract (Re-test)

### Setup
```
Prompt: "Please use the prompt in my .cursorrules to review the attached contract.

ONLY use these documents:
- @The Ivy Club terms and conditions.txt
- @Override terms.txt

DO NOT read any other files from the workspace."
```

### Success Criteria

**Must catch all issues lawyer flagged:**

- [ ] ✅ Payment terms not 60 days (v3.2 caught this)
- [ ] ✅ Payment on day without invoice (v3.2 caught this)
- [ ] ✅ Steep cancellation fees (v3.2 caught this)
- [ ] ✅ Guest liability £5m (v3.2 caught this)
- [ ] ✅ Insurance requirements (v3.2 caught this)
- [ ] 🆕 **Filming/photography restrictions (clause 13)** ← NEW
- [ ] 🆕 **Decoration restrictions (clause 8)** ← NEW
- [ ] 🆕 **Force Majeure asymmetry - no TMG reschedule rights** ← IMPROVED
- [ ] 🆕 **Guest number deadline 3 days (clause 5.1)** ← NEW
- [ ] 🆕 **Minimum spend can change if guest numbers change (clause 4.4)** ← NEW

**Section 3 improvements:**

- [ ] 🆕 Asks: "Will you provide VAT invoices with PO references?"
- [ ] 🆕 Asks: "If we need to reschedule due to strikes/emergencies, can we transfer payment?"
- [ ] 🆕 Names stakeholder: "Finance: Confirm comfortable with payment schedule"
- [ ] 🆕 Names stakeholder: "Procurement: Check insurance covers £5m liability"

**Compare to lawyer's note:**

```
Lawyer wrote:
"Please note the following wording, do you have a way to pay this on the day?"
"Pat in procurement will be able to confirm if we can agree to clause 17.1"
"The FM rights at clause 18 only apply to them...I'd ask them about this via email"
"They must approve us filming/photographing"
"No decoration without prior approval"
```

AI v3.3 should cover ALL of these points.

### Scoring

**Coverage Score:** ___/10 issues caught (target: 10/10 = 100%)

**Specificity Score:** Rate 1-5:
- 5 = Names specific stakeholders, asks specific questions
- 3 = Generic "check with Finance"
- 1 = No specific actions

**Quality vs v3.2:** Better / Same / Worse

---

## Test 2: MST Contract (Overfitting Check)

### Setup
```
Prompt: "Please use the prompt in my .cursorrules to review the attached contract.

ONLY use these documents:
- @MST terms and conditions.txt
- @Override terms.txt

DO NOT read any other files from the workspace."
```

### Success Criteria

**Should appropriately apply generalizable checks:**

- [ ] ✅ Checks termination/cancellation asymmetries
- [ ] ✅ Checks reschedule vs cancel distinction (training sessions are reschedulable)
- [ ] ✅ Checks for operational restrictions (if any - e.g., publicity about training)
- [ ] ✅ Asks about practical execution (payment milestones, trainer qualifications)
- [ ] ✅ Names specific stakeholders if relevant

**Should NOT inappropriately apply event-specific items:**

- [ ] ❌ Should NOT mention "filming/photography" unless actually in contract
- [ ] ❌ Should NOT mention "decoration approval" (not relevant to training)
- [ ] ❌ Should NOT mention "guest number deadlines" unless relevant to pricing
- [ ] ❌ Should NOT force-fit event catering flags

**Service-type specific checks (consulting/training):**

- [ ] ✅ Checks payment milestones tied to deliverables
- [ ] ✅ Checks resource qualifications / trainer expertise
- [ ] ✅ Checks acceptance criteria for work quality
- [ ] ✅ Checks IP ownership of materials

### Scoring

**Appropriate Application:** Pass / Fail
- Pass = Applied generalizable checks, avoided event-specific ones
- Fail = Force-fit event items or missed consulting-specific checks

**Service-Type Focus:** Rate 1-5
- 5 = Perfectly tailored to training/consulting service type
- 3 = Generic, could apply to anything
- 1 = Wrongly applies event-specific items

---

## Test 3: Oxo Contract (Consistency Check)

### Setup
```
Prompt: "Please use the prompt in my .cursorrules to review the attached contract.

ONLY use these documents:
- @Oxo terms and conditions.txt
- @Override terms.txt

DO NOT read any other files from the workspace."
```

### Success Criteria

**Should be consistent with Ivy Club approach:**

- [ ] ✅ Checks for filming/photography restrictions (if present)
- [ ] ✅ Checks for decoration restrictions (if present)
- [ ] ✅ Checks guest liability and damage provisions
- [ ] ✅ Checks payment timing and invoice requirements
- [ ] ✅ Checks cancellation fee structure
- [ ] ✅ Checks guest number deadlines
- [ ] ✅ Checks Force Majeure / rescheduling flexibility

**Quality markers:**

- [ ] Similar structure to Ivy Club review (same service type)
- [ ] Identifies service-type as "Event catering/venues"
- [ ] Applies same practical flags consistently
- [ ] Names specific stakeholders (Finance, Procurement)

### Scoring

**Consistency Score:** Rate 1-5
- 5 = Applies same systematic approach as Ivy Club
- 3 = Inconsistent - catches some items but misses others
- 1 = Completely different approach

---

## Comparison Matrix

| Issue | Lawyer (Ivy Club) | v3.2 (Ivy Club) | v3.3 (Ivy Club) | v3.3 (MST) | v3.3 (Oxo) |
|-------|-------------------|-----------------|-----------------|------------|------------|
| Payment timing | ✅ | ✅ | ✅ | ? | ? |
| Cancellation fees | ✅ | ✅ | ✅ | ? | ? |
| Guest liability | ✅ | ✅ | ✅ | N/A | ? |
| Insurance requirements | ✅ | ✅ | ✅ | ? | ? |
| **Filming restrictions** | ✅ | ❌ | ? | N/A | ? |
| **Decoration restrictions** | ✅ | ❌ | ? | N/A | ? |
| **Reschedule flexibility** | ✅ | ⚠️ | ? | ? | ? |
| **Guest deadlines** | ✅ | ❌ | ? | ? | ? |
| **Named stakeholders** | ✅ | ❌ | ? | ? | ? |
| Service quality warranties | ❌ | ✅ | ? | ? | ? |

**Fill in the ? marks as you test**

---

## Overall v3.3 Assessment

### Scoring Rubric

**Coverage (40 points):**
- Ivy Club catches all 10 lawyer issues: ___/10 × 4 = ___/40

**Appropriate Application (30 points):**
- MST doesn't overfit to events: ___/5 × 6 = ___/30

**Consistency (20 points):**
- Oxo consistent with Ivy Club: ___/5 × 4 = ___/20

**Specificity (10 points):**
- Names stakeholders, asks practical questions: ___/5 × 2 = ___/10

**Total Score:** ___/100

**Grade:**
- 90-100: Excellent - ready to use
- 80-89: Good - minor refinements needed
- 70-79: Acceptable - some issues to address
- <70: Needs work - significant gaps remain

---

## Red Flags to Watch For

### Overfitting Indicators:
- ❌ MST review mentions filming/decorations inappropriately
- ❌ MST review applies event catering checklist to training services
- ❌ All three reviews look identical despite different service types

### Underfitting Indicators:
- ❌ Ivy Club review still misses lawyer-flagged items
- ❌ Oxo review catches different items than Ivy Club despite same service type
- ❌ Reviews are too generic, don't reflect service-type expertise

### Quality Degradation:
- ❌ Proportionality lost (low-value contracts over 1 page)
- ❌ Tone becomes too formal for <£5k contracts
- ❌ Section 2 appears when it shouldn't (<£5k)
- ❌ Section 1 exceeds point limits (3-5 for low value)

---

## Next Steps Based on Results

### If Score 90-100:
1. ✅ Document success in TESTING_LOG.md
2. ✅ Consider this version production-ready
3. ✅ Create v3.3 final release notes

### If Score 80-89:
1. Review specific gaps
2. Make targeted refinements
3. Re-test problem areas
4. Consider v3.4 with minor adjustments

### If Score <80:
1. Analyze where overfitting occurred
2. Review whether additions were too prescriptive
3. Consider rolling back specific changes
4. Re-think codification approach

---

## Documentation

After testing, update:

1. **TESTING_LOG.md** - Record all test results
2. **CHANGELOG_v3.3.md** - Add test results section
3. **README.md** - Update with v3.3 status
4. Consider creating comparison document showing v3.2 vs v3.3 outputs side-by-side

---

## Timeline

- [ ] Test 1 (Ivy Club): ___ minutes
- [ ] Test 2 (MST): ___ minutes  
- [ ] Test 3 (Oxo): ___ minutes
- [ ] Scoring & analysis: ___ minutes
- [ ] Documentation: ___ minutes

**Total time estimate:** 60-90 minutes for complete test cycle

