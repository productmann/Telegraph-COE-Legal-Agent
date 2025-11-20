# Version Comparison: v3.3 → v4.0 with questions

## Overview

**v3.3:** Contract value-based proportionality (comprehensive legal review scaled to contract size)

**v4.0:** Context-aware adaptive review (asks 3 questions to match business reality)

---

## What's New in v4.0

### 🆕 NEW: Step 0 - Context Gathering

**v4.0 asks 3 questions before reviewing:**

1. **Timeline:** Sign today / this week / 1-2 weeks / just gathering info
2. **Vendor Relationship:** Repeat-good / Repeat-issues / New / Unsure
3. **Decision Type:** Sign vs don't / Sign vs negotiate / Informational / Negotiation prep

**Exception:** If email/correspondence provided, extracts context automatically.

### 🆕 NEW: Five Review Modes

| Mode | Trigger | Output |
|------|---------|--------|
| **PRAGMATIC** | Sign today + repeat vendor ✅ | 3 risks, skip Section 2, 1 page |
| **CAUTIOUS** | Sign today + new vendor 🆕 | 5 risks, essential gaps, 1.5 pages |
| **STANDARD** | 1-2 weeks + repeat vendor ✅ | 5 risks, focused gaps |
| **COMPREHENSIVE** | 1-2 weeks + new vendor 🆕 | 5-6 risks, full review |
| **INFORMATIONAL** | Just gathering info 📋 | Full analysis for reference |

### 🔄 UPDATED: CONTRACT ASSESSMENT Template

**v3.3 had:**
```
- Contract value: £___
- Value tier: Low/Medium/High
- Service type: [type]
- Include Section 2: YES/NO
- Max Section 1 points: 3-5 / 5-6
- Tone: Collaborative / Professional
- Page limit: 1 / 2 / 3+ pages
```

**v4.0 adds:**
```
- Timeline: [NEW]
- Vendor relationship: [NEW]
- Decision type: [NEW]
- Review mode: [NEW - PRAGMATIC/CAUTIOUS/STANDARD/COMPREHENSIVE/INFORMATIONAL]
- Include Section 2: YES/NO/MINIMAL [UPDATED - context-aware]
- Max Section 1 points: [UPDATED - mode-specific]
- Tone: [UPDATED - mode-appropriate]
- Page limit: [UPDATED - mode-specific]
```

### 🔄 UPDATED: Section 2 Logic

**v3.3:** Based purely on contract value
- <£5k: Skip Section 2
- £5k-£10k: 5-8 gaps
- £10k-£50k: 10-20 gaps
- >£50k: Comprehensive

**v4.0:** Based on contract value AND context
- PRAGMATIC mode: Skip or minimal (5 items) regardless of value
- CAUTIOUS mode: Essential gaps only (8-10)
- STANDARD/COMPREHENSIVE: Per contract value tier
- INFORMATIONAL: Comprehensive regardless of urgency

### 🔄 UPDATED: Self-Check (Step 6)

**v3.3 checked:**
- Contract assessment output ✓
- Asymmetries identified ✓
- Service-type flags ✓
- Section 2 decision tree ✓
- Tone appropriate ✓
- Scenario-based Section 1 ✓

**v4.0 adds:**
- Did I gather context or extract from documents? [NEW]
- Does review mode match timeline + vendor? [NEW]
- Is tone appropriate for review mode? [ENHANCED]
- Does recommendation match decision type? [NEW]

---

## Side-by-Side Workflow Comparison

### v3.3 Workflow
```
1. Read contract
2. Assess value & service type
3. Identify asymmetries
4. Check practical commercial issues
5. Check Override Terms
6. Structure output (value-based)
7. Self-check
8. Deliver review
```

### v4.0 Workflow
```
0. ASK CONTEXT QUESTIONS (or extract from emails) ← NEW
1. Read contract
2. Assess value & service type + CONTEXT ← ENHANCED
3. Identify asymmetries
4. Check practical commercial issues
5. Check Override Terms
6. Structure output (context-aware) ← ENHANCED
7. Self-check (including context verification) ← ENHANCED
8. Deliver mode-appropriate review ← ENHANCED
```

---

## Real-World Examples

### Example: MST Training Contract (£26,808)

#### v3.3 Output (Value-Based Only)
```
CONTRACT ASSESSMENT:
- Value: £26,808
- Tier: Medium
- Service: Consulting
- Section 2: YES (10-20 gaps)
- Section 1: 5-6 points
- Tone: Professional

→ Delivers 5 business risks + 20+ legal gaps
→ Recommends "Negotiate before signing"
→ ~2 pages
```

#### v4.0 Output (Context-Aware)

**Scenario A: "Sign today, used them before"**
```
CONTRACT ASSESSMENT:
- Value: £26,808
- Tier: Medium
- Timeline: Sign today ← NEW
- Vendor: Repeat-good ← NEW
- Mode: PRAGMATIC ← NEW
- Section 2: MINIMAL (5 items)
- Section 1: 3 points
- Tone: Collaborative

→ Delivers 3 key risks + 5 priority gaps
→ Recommends "Acceptable to sign given context"
→ ~1 page
```

**Scenario B: "Have 2 weeks, never used them"**
```
CONTRACT ASSESSMENT:
- Value: £26,808
- Tier: Medium
- Timeline: 1-2 weeks ← NEW
- Vendor: New ← NEW
- Mode: COMPREHENSIVE ← NEW
- Section 2: YES (full review)
- Section 1: 5-6 points
- Tone: Professional

→ Delivers 5-6 business risks + 20 legal gaps
→ Recommends "Negotiate X, Y, Z before signing"
→ ~2 pages
```

**Same contract → Different output based on business context**

---

## Key Benefits of v4.0

### 1. Matches Real Legal Practice
**v3.3:** Always delivered comprehensive review regardless of urgency
**v4.0:** Mirrors how real lawyers triage (like Melonie's pragmatic MST email)

### 2. Avoids "Over-Lawyering"
**v3.3:** £26k contract got full legal audit even for "sign today" scenarios
**v4.0:** Delivers pragmatic "risks to be aware of" when appropriate

### 3. Context-Driven Recommendations
**v3.3:** Recommendations based only on contract terms
**v4.0:** Recommendations consider timeline, vendor track record, decision type

### 4. Explicit Trade-Off Framing
**v3.3:** "Here are the gaps, recommend negotiating"
**v4.0:** "Cost of delay vs value of improvements" (when appropriate)

### 5. Auto-Extract from Emails
**v3.3:** No document context awareness
**v4.0:** Reads email threads to extract timeline/vendor info automatically

---

## What Stays the Same

✅ **Contract value tiers** still apply (Low/Medium/High)
✅ **Service-type focus** still tailored (events/SaaS/consulting/goods)
✅ **Asymmetries-first approach** unchanged
✅ **Scenario-based Section 1** format unchanged
✅ **Override Terms compliance** still systematic
✅ **Proportionality principle** enhanced (not replaced)

---

## Migration Guide

### For Users
**No action required** - v4.0 is backward compatible:
- If you skip the questions, agent proceeds with default comprehensive mode
- If you provide email context, agent extracts info automatically
- Existing workflows continue to work

### For Testing
Update test scenarios to include context:

**Old test (v3.3):**
```
"Review @MST contract @Override terms"
```

**New test (v4.0):**
```
"Review @MST contract @Override terms @RE_ MST agreement.txt"
(Email contains context: "needs to be signed today" + "used MST before")

Expected: PRAGMATIC mode, 3 risks, 1 page
```

---

## File Naming Convention

- **v3.3 and earlier:** `Prompt - Legal_ Low Contract Value (vX.X).md`
- **v4.0:** `Prompt - Legal_ Low Contract Value (v4.0 with questions).md`

The "with questions" suffix indicates the context-gathering capability.

---

## Version History

| Version | Date | Key Feature |
|---------|------|-------------|
| v1.0 | - | Original prompt |
| v2.0 | - | Added proportionality by contract value |
| v3.0 | - | Added asymmetries-first approach |
| v3.1 | - | Enhanced service-type practical flags |
| v3.2 | - | Refined Section 1 scenario-based format |
| v3.3 | - | Improved tone guidance and self-check |
| **v4.0** | **Nov 18, 2025** | **Added context gathering (3 questions) + 5 review modes** |

---

## Bottom Line

**v3.3:** "One size fits most" - scaled by contract value only

**v4.0:** "Right review for your situation" - scaled by value AND context

The MST contract comparison proved v3.3 was sometimes "over-lawyered" for urgent, low-risk situations. v4.0 fixes this by asking 3 questions upfront to deliver the appropriate review depth.

