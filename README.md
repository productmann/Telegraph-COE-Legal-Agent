# Contract Review Agent - Low Value Contracts

This Cursor project is designed for iterating on and testing an AI agent that reviews low-value contracts against the Telegraph's standard terms.

## Purpose

The agent reviews third-party vendor contracts to identify deviations from our standard "Override terms" and generates internal memos highlighting key risks and issues.

## Project Structure

### Core Agent Files
- **`.cursorrules`** - The agent prompt that instructs Cursor's AI on how to review contracts
- **`Override terms.pdf`** - The company's standard terms document that serves as the reference
- **`Prompt - Legal_ Low Contract Value (1).txt`** - Original prompt (redundant with .cursorrules but kept for reference)

### Test Contracts
Sample contracts for testing the agent:
- `MST terms and conditions.pdf`
- `Oxo terms and conditions.pdf`
- `The Ivy Club terms and conditions.pdf`

### Supporting Documents
- Email threads and correspondence related to each contract

## How to Use This Project

### Testing the Agent

1. **Open a new chat** in Cursor (the `.cursorrules` file is automatically loaded)
2. **Reference a contract** you want reviewed, e.g.:
   ```
   Please review @MST terms and conditions.pdf against our override terms
   ```
3. **Review the output** - The agent will generate a memo following the format in `.cursorrules`
4. **Iterate** - If the output isn't right, adjust `.cursorrules` and test again

### Improving the Agent

1. **Edit `.cursorrules`** to refine the prompt
2. **Test with sample contracts** to validate changes
3. **Document learnings** - Add notes below about what works/doesn't work

## Testing Notes

### What to Test For

**Section 1 - KEY BUSINESS RISKS:**
- [ ] 3-6 points maximum (concise, not comprehensive)
- [ ] Each point starts with bold scenario-based title
- [ ] Leads with "what could go wrong" before citing Override terms
- [ ] Uses plain English (no legalese)
- [ ] Focuses on operational/financial/commercial risks
- [ ] Highlights asymmetric or imbalanced terms
- [ ] Combines related issues (not scattered)

**Section 2 - COMPREHENSIVE OVERRIDE TERMS REVIEW:**
- [ ] Covers ALL remaining Override Terms gaps
- [ ] Organized by topic (liability, data protection, termination, etc.)
- [ ] Nothing omitted from Override Terms
- [ ] Concise but complete (one sentence per issue is fine)
- [ ] More technical/legal language is acceptable here

### Known Issues / Observations
(Add notes here as you test)

---

## Quick Commands

**Review a specific contract:**
```
Review @[contract-name.pdf] against override terms
```

**Compare two outputs:**
```
Compare your previous review of [contract] to the current one - what changed?
```

**Test specific sections:**
```
Focus on liability and indemnification clauses in @[contract-name.pdf]
```

