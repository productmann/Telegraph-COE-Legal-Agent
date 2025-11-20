# Opener Comparison: v3.1 vs v3.2

## The Problem

The v3.1 opener misleadingly framed the task as "Override Terms compliance checking" rather than "business risk assessment," which caused the agent to pattern-match to standard legal audit templates.

---

## Side-by-Side Comparison

### v3.1 Opener ❌

```
You are a legal contract review assistant for internal business teams. 
Your role is to review third-party contracts against the company's 
standard terms outlined in the "Override terms.pdf" document and 
generate a concise memo highlighting key issues and deviations.

## Business Context

You are supporting internal business teams who need to make fast 
commercial decisions. Your role is to:
- Highlight practical risks that could impact day-to-day operations
- Flag imbalanced commercial terms that create business exposure
- Explain what could go wrong in plain English
- Help stakeholders weigh "sign today with gaps" vs "negotiate and delay"

Remember: A tight 5-point business risk summary that influences the 
decision is better than a 15-point legal audit that gets ignored.
```

**What this implies:**
1. ❌ Primary task = "review against Override terms.pdf"
2. ❌ Start with compliance checking
3. ❌ Bullets are secondary context (not primary goals)
4. ❌ No explicit statement of what NOT to do
5. ❌ Framing suggests: "Check Override Terms → Identify gaps → Write memo"

---

### v3.2 Opener ✅

```
You are a legal contract review assistant supporting internal business 
teams who need to make fast commercial decisions on third-party contracts.

Your role is to:
1. Identify practical business risks (asymmetries, financial exposure, 
   operational constraints)
2. Flag critical deviations from the company's standard terms 
   ("Override terms.pdf")
3. Help stakeholders weigh "sign today with gaps" vs "negotiate and delay"

You are NOT producing a comprehensive legal audit—you're providing 
decision-focused business guidance scaled to contract value and service type.

## Business Context

Remember: A tight 5-point business risk summary that influences the 
decision is better than a 15-point legal audit that gets ignored.
```

**What this implies:**
1. ✅ Primary audience = "business teams making fast decisions"
2. ✅ Numbered priorities: business risks FIRST, Override Terms SECOND
3. ✅ Explicit negative statement: "You are NOT producing legal audit"
4. ✅ Clear framing: "decision-focused business guidance"
5. ✅ Workflow suggestion: "Identify risks → Flag critical deviations → Support decision"

---

## Key Differences

| Aspect | v3.1 | v3.2 |
|--------|------|------|
| **First sentence subject** | "review third-party contracts" | "supporting business teams" |
| **First action verb** | "review against...standard terms" | "make fast commercial decisions" |
| **Override Terms position** | Sentence 1 (primary focus) | Item #2 (secondary check) |
| **Business risks position** | Buried in bullets | Item #1 (primary focus) |
| **Explicit NOT statement** | Missing | "You are NOT producing legal audit" |
| **Framing** | Compliance audit | Decision support |
| **Implied workflow** | Check Override Terms → Find gaps | Assess business risks → Flag critical gaps |

---

## Impact on Agent Behavior

### v3.1 Behavior (Observed)

When I read v3.1, my mental model was:
1. "I need to check Override Terms compliance"
2. "Let me read the contract and see what's missing"
3. "Now I'll write a memo documenting all the gaps"
4. **Result:** Standard legal audit template (wrong approach)

### v3.2 Behavior (Expected)

When I read v3.2, my mental model should be:
1. "I'm helping a business team make a sign/don't-sign decision"
2. "What practical risks exist? What asymmetries?"
3. "Which Override Terms gaps actually matter for THIS contract?"
4. **Result:** Business-focused risk assessment (correct approach)

---

## Why Word Order Matters

The opener is the **anchor point** that frames everything that follows. Compare:

**Bad framing (v3.1):**
> "Your role is to **review contracts against standard terms**...and also support business teams"

This reads as: Legal compliance is primary, business support is secondary.

**Good framing (v3.2):**
> "Your role is to **support business teams**...by identifying risks and flagging critical deviations"

This reads as: Business support is primary, compliance checking is a tool to achieve that.

---

## Testing Hypothesis

**Hypothesis:** The v3.2 opener will reduce pattern-matching to "standard legal review" templates by reframing the primary goal.

**Test:** Run the same contract (Ivy Club £2k) through v3.2 and check if:
- ✅ Step 1 assessment correctly identifies <£5k tier
- ✅ Asymmetries are identified BEFORE Override Terms review
- ✅ Section 2 is skipped (as appropriate for <£5k)
- ✅ Tone is collaborative (not formal legal language)
- ✅ Focus is on business decisions (not comprehensive compliance)

**Expected improvement:** The opener + workflow together should create the right mental model from the start.

