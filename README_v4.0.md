# Legal Contract Review Assistant v4.0 - Low Contract Value (with questions)

## What's New in v4.0 🎯

**v4.0 introduces context-aware contract review** - the agent now asks 3 questions to deliver the right review for your actual business situation.

### The 3 Questions

Before reviewing any contract, the agent asks:

1. **Timeline:** What's your timeline for signing?
2. **Vendor Relationship:** Have you worked with this vendor before?
3. **Decision Type:** What decision are you making?

Then delivers one of 5 review modes based on your answers.

---

## Quick Start

### Option 1: Answer the Questions

```
You: "Review this contract @MST terms.txt @Override terms.txt"

Agent: "To tailor this review to your needs, please confirm:
1. Timeline: What's your timeline for signing?
   - Need to sign today/tomorrow
   - Need to sign this week
   - Have 1-2 weeks to negotiate
   - Just gathering information

2. Vendor Relationship: Have you worked with this vendor before?
   - Yes - good experience
   - Yes - had issues previously
   - No - first time vendor
   - Unsure

3. Decision Type: What decision are you making?
   - Sign as-is vs don't sign
   - Sign as-is vs negotiate
   - Just need to understand the risks
   - Need ammunition/talking points for negotiation"

You: "1. Sign today, 2. Yes - good experience, 3. Sign as-is vs don't sign"

Agent: [Delivers PRAGMATIC review - 3 risks, 1 page, "acceptable to sign given..."]
```

### Option 2: Provide Email Context (Auto-Extract)

```
You: "Review @MST terms.txt @Override terms.txt @RE_ MST agreement.txt"

Agent: [Reads email, extracts "sign today" + "used before", delivers PRAGMATIC review automatically]
```

---

## The 5 Review Modes

| Your Context | Agent Mode | What You Get |
|--------------|------------|--------------|
| Sign today + repeat vendor ✅ | **PRAGMATIC** | 3 key risks, 1 page, "acceptable to sign if..." |
| Sign today + new vendor 🆕 | **CAUTIOUS** | 5 risks, essential gaps, 1.5 pages |
| 1-2 weeks + repeat vendor ✅ | **STANDARD** | 5 risks, focused gaps, negotiate easy wins |
| 1-2 weeks + new vendor 🆕 | **COMPREHENSIVE** | 5-6 risks, full review, negotiate priorities |
| Just gathering info 📋 | **INFORMATIONAL** | Full analysis for reference |

---

## Real Example: MST Training Contract (£26,808)

### Scenario A: "Sign today, used them before"

**Context:**
- Timeline: Sign today
- Vendor: Repeat - good experience
- Decision: Sign vs don't sign

**Output (PRAGMATIC MODE):**
- 3 key risks to be aware of
- Skip Section 2 (or 5 priority gaps only)
- Collaborative tone
- Recommendation: "Acceptable to sign given repeat vendor and time constraints"
- 1 page

### Scenario B: "Have 2 weeks, never used them"

**Context:**
- Timeline: 1-2 weeks
- Vendor: New
- Decision: Sign vs negotiate

**Output (COMPREHENSIVE MODE):**
- 5-6 business risks
- Full Section 2 (20 gaps)
- Professional tone
- Recommendation: "Recommend negotiating X, Y, Z before signing"
- 2 pages

**Same contract → Different review based on business reality**

---

## How It Works

### The Workflow

```
┌─────────────────────────────────────┐
│ 0. CONTEXT GATHERING (NEW in v4.0) │
│    Ask 3 questions OR extract from │
│    email correspondence             │
└──────────────┬──────────────────────┘
               ↓
┌─────────────────────────────────────┐
│ 1. CONTRACT ASSESSMENT              │
│    Value + Service Type + CONTEXT   │
│    → Determines Review Mode         │
└──────────────┬──────────────────────┘
               ↓
┌─────────────────────────────────────┐
│ 2-4. RISK ANALYSIS                  │
│    Asymmetries → Practical Issues   │
│    → Override Terms Compliance      │
└──────────────┬──────────────────────┘
               ↓
┌─────────────────────────────────────┐
│ 5. MODE-APPROPRIATE OUTPUT          │
│    PRAGMATIC: 3 risks, 1 page       │
│    COMPREHENSIVE: 6 risks, 2+ pages │
└─────────────────────────────────────┘
```

### Decision Logic

```
IF sign today + repeat vendor (good):
   → PRAGMATIC: "Risks to be aware of"
   
IF sign today + new vendor:
   → CAUTIOUS: "Key risks you're accepting"
   
IF 1-2 weeks + repeat vendor:
   → STANDARD: "Business risks and easy wins"
   
IF 1-2 weeks + new vendor:
   → COMPREHENSIVE: "Full analysis"
   
IF just gathering info:
   → INFORMATIONAL: "Full analysis for reference"
```

---

## Why v4.0?

### Problem with v3.3

**MST contract review comparison:**

| Aspect | Lawyer's Email (Real World) | v3.3 Agent Output | Gap |
|--------|----------------------------|-------------------|-----|
| Risks flagged | 3 key practical risks | 5 risks + 25 legal gaps | Too comprehensive |
| Recommendation | "Sign today given context" | "Negotiate before signing" | Wrong for urgency |
| Length | Short email (~1 page) | 2+ page legal memo | Too long |
| Tone | Pragmatic, peer-to-peer | Professional legal | Too formal |

**Root cause:** Agent had no business context (timeline, vendor history, urgency)

### Solution in v4.0

✅ **Ask context questions** to understand the actual business decision
✅ **Deliver appropriate depth** - pragmatic when urgent, comprehensive when time permits
✅ **Match real legal practice** - like how Melonie triaged the MST contract
✅ **Right recommendation** - "acceptable to sign" vs "negotiate first" based on context

---

## File Structure

```
Legal - Low Contract Value/
├── .cursorrules                                          ← v4.0 agent prompt
├── Prompt - Legal_ Low Contract Value (v4.0 with questions).md  ← Standalone v4.0
├── Prompt - Legal_ Low Contract Value (v3.2).md         ← Previous versions
├── Prompt - Legal_ Low Contract Value (v3.1).md
├── Prompt - Legal_ Low Contract Value (v2.0).md
├── archive/
│   └── Prompt - Legal_ Low Contract Value (1).txt       ← v1.0
├── CHANGELOG_v3.4_CONTEXT_GATHERING.md                  ← Detailed changes
├── IMPLEMENTATION_SUMMARY_v3.4.md                       ← Implementation guide
├── VERSION_COMPARISON_v3_to_v4.md                       ← Side-by-side comparison
├── reference-documents/
│   ├── Override terms.pdf
│   └── Override terms.txt
└── test-contracts/
    ├── mst/
    │   ├── MST terms and conditions.txt
    │   └── RE_ MST agreement.txt                        ← Context document
    ├── oxo/
    └── ivy-club/
```

---

## Testing v4.0

### Test Case 1: MST with Email Context

**Input:**
```
Review @MST terms.txt @Override terms.txt @RE_ MST agreement.txt
```

**Expected:**
- Auto-extracts: "sign today" + "used MST before"
- Delivers: PRAGMATIC mode
- Output: 3 risks, 1 page, "acceptable to sign given..."

### Test Case 2: MST without Context

**Input:**
```
Review @MST terms.txt @Override terms.txt
```

**Agent asks:**
- Timeline?
- Vendor relationship?
- Decision type?

**User answers:** "1-2 weeks, new vendor, sign vs negotiate"

**Expected:**
- Delivers: COMPREHENSIVE mode
- Output: 5-6 risks, full Section 2, "recommend negotiating..."

### Test Case 3: Low-Value Contract (<£5k)

**Expected behavior:**
- PRAGMATIC mode should still apply value-based rules
- Skip Section 2 even if comprehensive mode (unless red flags)
- Collaborative tone regardless of vendor

---

## Key Principles (Unchanged from v3.x)

✅ **Proportionality** - scale to contract value
✅ **Service-type focus** - tailor to what could go wrong
✅ **Asymmetries first** - flag one-sided terms
✅ **Scenario-based Section 1** - "If X happens..." not legal citations
✅ **Decision-focused** - influence sign/don't-sign, not academic audit

**New in v4.0:**
✅ **Context-aware** - match business reality
✅ **Five review modes** - from pragmatic to comprehensive
✅ **Auto-extract from emails** - no manual context entry needed

---

## Version History

| Version | Date | Key Feature |
|---------|------|-------------|
| v1.0 | - | Original prompt |
| v2.0 | - | Proportionality by contract value |
| v3.0 | - | Asymmetries-first approach |
| v3.3 | - | Refined format and tone guidance |
| **v4.0** | **Nov 18, 2025** | **Context gathering + 5 review modes** |

---

## Support Documents

- **`CHANGELOG_v3.4_CONTEXT_GATHERING.md`** - Detailed changelog
- **`IMPLEMENTATION_SUMMARY_v3.4.md`** - Implementation guide
- **`VERSION_COMPARISON_v3_to_v4.md`** - Side-by-side v3 vs v4
- **`TESTING_WORKFLOW.md`** - Testing instructions (update for v4.0)

---

## Quick Reference Card

### When to Use Each Mode

| Business Situation | Mode | Output |
|-------------------|------|--------|
| 🔥 **Urgent + Safe** (sign today, repeat vendor) | PRAGMATIC | 3 risks, 1 page |
| ⚠️ **Urgent + Risky** (sign today, new vendor) | CAUTIOUS | 5 risks, 1.5 pages |
| ⚖️ **Time + Safe** (1-2 weeks, repeat vendor) | STANDARD | 5 risks, easy wins |
| 📋 **Time + Risky** (1-2 weeks, new vendor) | COMPREHENSIVE | 6 risks, full review |
| 📚 **Research** (just gathering info) | INFORMATIONAL | Full analysis |

### The Questions (Memorize These)

1. **Timeline:** Today / Week / 1-2 weeks / Info
2. **Vendor:** Repeat-good / Repeat-issues / New / Unknown
3. **Decision:** Sign vs don't / Sign vs negotiate / Info / Negotiation prep

---

## Bottom Line

**v4.0 = Context-Aware Contract Review**

- Ask 3 questions (or read email context)
- Deliver right review for your situation
- Match how real lawyers triage urgent contracts
- No more "over-lawyering" when you need fast guidance

**Same rigor, smarter application.**

