# Testing Workflow Guide

## Quick Start: Testing the Agent

### 1. Review a Contract
In a new Cursor chat, type:
```
Review @test-contracts/mst/MST terms and conditions.pdf against @reference-documents/Override terms.pdf
```

### 2. Save the Output
Copy the agent's output to a new file in `test-outputs/`:
```
test-outputs/[ContractName]_[Date]_v[PromptVersion].txt
```

Example: `test-outputs/MST_2024-11-17_v2.0.txt`

### 3. Evaluate the Output
Use the checklist in `TESTING_LOG.md` to rate quality

### 4. Iterate on Prompt
Edit `.cursorrules` based on what needs improvement

### 5. Test Again
Repeat with the same contract to compare results

---

## Organized Testing Process

### Step-by-Step Testing Cycle

1. **Pick a test contract** from `test-contracts/`
2. **Note your current prompt version** in TESTING_LOG.md
3. **Run the review** in a new Cursor chat
4. **Save output** to `test-outputs/` with naming convention
5. **Evaluate** using the quality checklist
6. **Document** findings in TESTING_LOG.md
7. **Iterate** on `.cursorrules` if needed
8. **Retest** to validate improvements

### File Naming Conventions

**Test Outputs:**
```
[VendorName]_[YYYY-MM-DD]_v[PromptVersion]_[Optional-Notes].txt
```

Examples:
- `MST_2024-11-17_v2.0.txt`
- `MST_2024-11-17_v2.1_improved-liability.txt`
- `Oxo_2024-11-17_v2.0_baseline.txt`

**Benefits:**
- Easy chronological sorting
- Clear version tracking
- Ability to compare outputs from different prompt versions

---

## Quality Evaluation Checklist

### Section 1: KEY BUSINESS RISKS ⭐⭐⭐⭐⭐

- [ ] **Length**: 3-6 points only (not more)
- [ ] **Format**: Bold scenario title + 1-2 sentences + brief citation
- [ ] **Lead with scenario**: "If X happens, Y result" before citing Override Terms
- [ ] **Plain English**: No legalese (avoid "pursuant to", "notwithstanding", etc.)
- [ ] **Business focus**: Operational/financial/commercial risks, not just legal gaps
- [ ] **Asymmetries highlighted**: Imbalanced terms that create unfair exposure
- [ ] **Combined issues**: Related items grouped (not scattered across multiple bullets)
- [ ] **Actionable**: Each risk helps with sign/don't-sign decision

### Section 2: COMPREHENSIVE OVERRIDE TERMS REVIEW ⭐⭐⭐⭐⭐

- [ ] **Complete coverage**: ALL Override Terms deviations documented
- [ ] **Organized**: Grouped by topic (liability, data protection, termination, etc.)
- [ ] **Concise**: One sentence per issue is fine
- [ ] **Nothing omitted**: Comprehensive legal documentation
- [ ] **Technical OK**: More legal language acceptable here

### Overall Quality ⭐⭐⭐⭐⭐

- [ ] **No greeting/closing**: Gets straight to the issues
- [ ] **Subject line**: "RE: [Vendor] - [Contract Type]" format
- [ ] **Tone**: Section 1 conversational, Section 2 technical
- [ ] **Accuracy**: Correctly identifies deviations from Override Terms
- [ ] **No duplicates**: Issues not repeated across sections

---

## Testing Scenarios

### Scenario 1: Baseline Testing
**Goal:** Establish current performance level

1. Test all three contracts (MST, Oxo, Ivy Club)
2. Save outputs with consistent naming
3. Rate each output using quality checklist
4. Identify patterns in what works/doesn't work

### Scenario 2: Focused Iteration
**Goal:** Improve specific aspect of output

1. Pick one problem area (e.g., "Section 1 too legal, not business-focused")
2. Revise `.cursorrules` with targeted changes
3. Test with ONE contract
4. Compare before/after outputs
5. If improved, test with other contracts to validate

### Scenario 3: Edge Case Testing
**Goal:** Find where agent struggles

1. Test with unusual contract types
2. Test with very short contracts
3. Test with contracts that heavily deviate from Override Terms
4. Document edge cases in TESTING_LOG.md

### Scenario 4: Comparative Testing
**Goal:** Compare different prompt versions

1. Save current `.cursorrules` as `archive/cursorrules_v[X.X].txt`
2. Make experimental changes
3. Test same contract with both versions
4. Save outputs with version numbers
5. Compare side-by-side
6. Keep best version, archive the other

---

## Common Testing Commands

### Review Commands
```
Review @test-contracts/mst/MST terms and conditions.pdf
```
```
Review @test-contracts/oxo/Oxo terms and conditions.pdf
```
```
Review @test-contracts/ivy-club/The Ivy Club terms and conditions.pdf
```

### Comparison Commands
```
Compare @test-outputs/MST_2024-11-17_v2.0.txt to @test-outputs/MST_2024-11-17_v2.1.txt
What improved? What got worse?
```

### Focused Testing Commands
```
Review only the liability and indemnification sections of @test-contracts/mst/MST terms and conditions.pdf
```
```
Focus on data protection compliance in @test-contracts/oxo/Oxo terms and conditions.pdf
```

---

## Tracking Improvements

### Version Control for .cursorrules

When making significant changes:

1. **Save current version:**
```bash
cp .cursorrules archive/cursorrules_v[X.X]_[YYYY-MM-DD].txt
```

2. **Note changes in TESTING_LOG.md:**
```markdown
**v2.1** - [Date]
- Added emphasis on combining related issues in Section 1
- Clarified "plain English" requirement with specific examples
- Added proportionality guidance
```

3. **Test new version** with at least one known contract

4. **Compare results** and decide whether to keep or revert

### Regression Testing

After major prompt changes, run all three test contracts to ensure:
- Improvements in target area
- No degradation in other areas
- Consistent quality across different contract types

---

## Tips for Effective Testing

### Do's ✅
- Test one change at a time
- Save all outputs with clear naming
- Use the same contracts for comparison
- Document what changed and why
- Take breaks between iterations (fresh eyes help)

### Don'ts ❌
- Don't make multiple prompt changes without testing between
- Don't skip documentation in TESTING_LOG.md
- Don't delete old outputs (disk space is cheap, data is valuable)
- Don't test with new contracts only (need baselines)
- Don't over-optimize for one contract (test across all three)

### Signs of Good Progress
- Section 1 reads like a business memo, not a legal audit
- Business stakeholder could make a decision from Section 1 alone
- Section 2 feels comprehensive but not overwhelming
- Output is consistent across different contract types
- Fewer revisions needed to get quality output

### Signs of Prompt Issues
- Agent produces 10+ points in Section 1 (too comprehensive)
- Section 1 full of legalese and citations
- Section 2 missing obvious Override Terms deviations
- Output format inconsistent between runs
- Agent asks clarifying questions instead of proceeding
- Agent provides suggestions instead of clear issue documentation

---

## Advanced Testing: A/B Testing Prompt Variations

When you have two competing approaches:

1. **Create variant:**
```bash
cp .cursorrules archive/cursorrules_v2.1a.txt
# Edit .cursorrules with approach A
```

2. **Test and save:**
```
Review @test-contracts/mst/MST terms and conditions.pdf
# Save to test-outputs/MST_2024-11-17_v2.1a.txt
```

3. **Create second variant:**
```bash
cp archive/cursorrules_v2.1a.txt archive/cursorrules_v2.1b.txt
cp archive/cursorrules_v2.1b.txt .cursorrules
# Edit .cursorrules with approach B
```

4. **Test and save:**
```
Review @test-contracts/mst/MST terms and conditions.pdf
# Save to test-outputs/MST_2024-11-17_v2.1b.txt
```

5. **Compare and choose winner**

---

## Quick Reference: File Organization

```
Legal - Low Contract Value/
├── .cursorrules                    # Active agent prompt
├── README.md                       # Project overview
├── TESTING_LOG.md                  # Test results & notes
├── TESTING_WORKFLOW.md            # This file
│
├── test-contracts/                 # Test cases
│   ├── mst/
│   │   ├── MST terms and conditions.pdf
│   │   ├── MST terms and conditions.txt
│   │   ├── RE_ MST agreement.pdf
│   │   └── RE_ MST agreement.txt
│   ├── oxo/
│   │   ├── Oxo terms and conditions.pdf
│   │   └── Re_ Oxo Gallery - Catering Contract 2024.pdf
│   └── ivy-club/
│       ├── The Ivy Club terms and conditions.pdf
│       └── RE_ The Ivy Club... contract signature.pdf
│
├── reference-documents/            # Standard terms
│   ├── Override terms.pdf
│   └── Override terms.txt
│
├── test-outputs/                   # Agent outputs
│   └── [saves go here with naming convention]
│
└── archive/                        # Old versions
    ├── Prompt - Legal_ Low Contract Value (1).txt
    ├── Prompt - Legal_ Low Contract Value (v2.0).md
    └── [old .cursorrules versions]
```


