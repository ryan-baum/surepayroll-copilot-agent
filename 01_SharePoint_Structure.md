# SharePoint Structure for SurePayroll Content Agent

## Overview
This document specifies the SharePoint site structure optimized for Copilot Studio RAG retrieval. Based on Microsoft's 36,000 character limit per file, documents are structured for optimal semantic search.

---

## Site Structure

```
SurePayroll Content System/
├── 📁 Core_Documentation/
│   ├── CONTEXT.md (Entry point - 8,500 chars)
│   ├── Content_Code.md (14,200 chars)
│   ├── Voice_Tone.md (11,800 chars)
│   ├── Grammar_Mechanics.md (9,400 chars)
│   ├── Inclusion_Accessibility.md (10,200 chars)
│   ├── Positioning.md (12,600 chars)
│   ├── Features_Benefits.md (15,300 chars)
│   ├── Quality_Standards.md (13,900 chars)
│   └── Workflow_Stages.md (11,100 chars)
│
├── 📁 Implementation_Research/
│   ├── Deep_Research_Synthesis.md (Key improvements - 14,800 chars)
│   └── Phase1_Implementation_Templates.md (if available)
│
└── 📁 Examples/ (NEW - Critical for quality)
    ├── Example_Brief_Strong.md
    ├── Example_Brief_Weak.md
    ├── Example_Outline_Strong.md
    ├── Example_Draft_Strong.md
    └── Example_Editorial_Review.md
```

---

## Document Optimization for RAG

### Required Changes to Existing Documents

Each document needs these additions at the TOP for better retrieval:

```markdown
---
Document: [Name]
Category: [Core Documentation | Implementation | Examples]
Topics: [comma-separated keywords]
Last Updated: [Date]
---

## Summary
[2-3 sentence overview of what this document covers]

## When to Use This Document
[Clear triggering conditions]

---

[Original content...]
```

### Example Header for Content_Code.md

```markdown
---
Document: Content_Code
Category: Core Documentation
Topics: editorial principles, content strategy, quality standards, CC1-CC7
Last Updated: 2026-02-05
---

## Summary
The 7 Content Code principles (CC1-CC7) that govern all SurePayroll content decisions. These are binary rules that determine whether content should be published.

## When to Use This Document
- Evaluating content quality at any stage
- Making editorial decisions about structure or messaging
- Resolving conflicts about content direction
- Training new team members on content standards

---

[Original content...]
```

---

## SharePoint Metadata Configuration

### Managed Metadata Terms

Create these term sets in SharePoint admin:

**Content Stage Term Set:**
- Briefing
- Outline
- First Draft
- Editorial Review
- Writer Revision
- Final Edit
- Published

**Document Type Term Set:**
- Core Reference
- Workflow Guide
- Example Content
- Research/Analysis

**Content Principle Term Set:**
- CC1-Move Readers Forward
- CC2-Justify Existence
- CC3-Think Like Owners
- CC4-Clarity First
- CC5-Clear POV
- CC6-Layered Credibility
- CC7-Answer Plus One

### Document Properties

Add these columns to the document library:

| Column Name | Type | Purpose |
|-------------|------|---------|
| ContentStage | Choice (metadata) | Which workflow stage uses this |
| DocumentType | Choice (metadata) | Type classification |
| CharacterCount | Number | Track file size for 36k limit |
| LastVerified | Date | When doc was last accuracy-checked |
| RelatedPrinciples | Multi-choice (metadata) | Which CC# principles apply |

---

## Creating Example Files (CRITICAL)

Based on research: 2-3 examples dramatically improve output quality. Create these NEW files:

### Example_Brief_Strong.md

```markdown
---
Document: Example_Brief_Strong
Category: Examples
Topics: brief, content planning, information gain
Purpose: Few-shot example of excellent brief
Last Updated: 2026-02-05
---

## Example: Strong Content Brief

### Metadata
- **Target Keyword:** "How to calculate overtime pay for salaried employees"
- **Content Type:** Blog post
- **Awareness Stage:** Problem-Aware
- **Target Persona:** Accidental Administrator
- **Word Count:** 1,500
- **Distribution Channel(s):** Organic search (primary), email newsletter (secondary)

### Strategic Foundation

**User Story:**
As a first-time employer who just hired a salaried employee, I want to understand when I owe them overtime so that I avoid wage violations and correctly budget labor costs.

**Three-Dimension Justification:**
- **Reader value:** Clarifies confusing FLSA exempt vs. non-exempt rules with salary threshold
- **Business value:** Problem-aware reader experiencing anxiety — perfect time to introduce SurePayroll's automatic overtime calculation
- **Landscape value:** Top 5 SERP results explain the rules but don't address the common mistake (assuming all salaried = exempt)

**Information Gain:**
Current SERP articles explain FLSA rules but don't address the #1 mistake small business owners make: assuming salaried = exempt. This piece will:
1. Lead with the costly mistake and real penalty example
2. Include Paychex data on how many small businesses miscategorize workers
3. Provide decision tree for determining exempt status (not in competitors)

### Content Requirements

**Working Title Options:**
1. "When Salaried Employees Qualify for Overtime (And How to Calculate It)"
2. "The Overtime Mistake That Costs Small Businesses Thousands"
3. "Salary Doesn't Mean Exempt: Your Guide to Overtime Rules"

**Thesis Statement:**
Paying someone a salary doesn't automatically make them exempt from overtime — here's how to know if you owe overtime and how to calculate it correctly.

**Required Sections:**
1. The costly assumption (lead with the mistake) — Why this matters
2. FLSA exempt criteria — The three-part test explained simply
3. Salary threshold for 2026 — Current number with history
4. Common job roles and their status — Specific examples readers can map to
5. How to calculate overtime for non-exempt salaried employees — Step-by-step with example
6. How to fix misclassification — Practical next steps
7. FAQ — Edge cases

**Key Points to Cover:**
- [ ] Current salary threshold ($844/week as of July 2024, subject to change)
- [ ] Three-part exemption test (salary basis, salary level, duties test)
- [ ] Common misconception that administrative assistant = administratively exempt
- [ ] Cost example: Real DOL penalty case
- [ ] How SurePayroll handles this automatically

**Questions to Answer:**
- What is the current salary threshold?
- What are the three tests for exemption?
- How do I calculate overtime for a non-exempt salaried employee?
- **[CC7 - Next Question]:** What do I do if I've been miscategorizing someone?

### Product Integration

**Natural Integration Point:**
In the "How to calculate" section — after explaining the manual calculation complexity, introduce: "SurePayroll automatically determines exempt status and calculates overtime based on your employee's salary and job duties. The system flags potential misclassifications during setup."

**Feature to Highlight:**
Automatic overtime calculation + exempt status guidance during employee setup

**Proof Point Available:**
"We've processed overtime for 500,000+ salaried non-exempt employees — the system knows the FLSA tests."

### Information Gain Verification (REQUIRED)

**1. Unique Contribution Test:**
- Contribution 1: Lead with the costly mistake (competitors lead with rules)
- Contribution 2: Decision tree for determining status (no competitor has this)
- Contribution 3: Paychex data on misclassification frequency among small businesses

**2. Primary Research Requirement:**
- Source: Paychex internal data on exempt vs non-exempt salaried employees
- Type: Proprietary data — "X% of small businesses with <10 employees incorrectly classify at least one worker"

**3. Kill Switch Check:**
✅ PASS — Three clear unique contributions identified, proprietary data available

### Quality Cliff Assessment

- **Topic difficulty:** High cliff (competing against established HR/payroll sites)
- **Mandatory differentiator:** Paychex data + decision tree tool
- **Minimum quality threshold:** Must include proprietary insight and visual decision aid

### SEO & Linking

**Search Intent:** Informational (learning) → Commercial investigation (considering solutions)

**Internal Links to Include:**
- "How to set up payroll for the first time" — link from employee setup mention
- "FLSA compliance guide" — link from three-part test section
- "Employee classification: W-2 vs 1099" — link from related topic

**Competitor Content Gaps:**
Top SERP results (Indeed, ADP, Paychex.com) explain the rules but:
- Don't lead with the common mistake
- Don't provide decision-making framework
- Are written for HR professionals, not first-time employers

### Constraints & Notes

**Compliance Considerations:**
- Cannot say "this guarantees compliance"
- Must include disclaimer: "Consult your employment attorney for specific situations"
- Cite DOL regulations accurately with current year

**SME Requirements:**
Need verification on:
1. Current salary threshold for 2026 (check if updated from July 2024 rule)
2. Paychex data stat accuracy
3. Decision tree logic accuracy

**Notes for Writer:**
- Tone: Confident and reassuring (this is confusing but solvable)
- Avoid HR jargon — write for someone who's never heard "administratively exempt"
- Use specific job titles in examples (office manager, bookkeeper, project coordinator)
```

---

### Example_Brief_Weak.md (Shows what NOT to do)

```markdown
---
Document: Example_Brief_Weak
Category: Examples
Topics: brief, content planning, what to avoid
Purpose: Few-shot example of inadequate brief (for contrast)
Last Updated: 2026-02-05
---

## Example: Weak Content Brief (DO NOT EMULATE)

### Metadata
- **Target Keyword:** "small business payroll tips"
- **Content Type:** Blog post
- **Awareness Stage:** Unaware
- **Target Persona:** Small business owners
- **Word Count:** 1,000-1,500
- **Distribution Channel(s):** Organic search

### Strategic Foundation

**User Story:**
As a small business owner, I want payroll tips so that I can do payroll better.

❌ **Why this fails:** Vague goal, no specific job-to-be-done, "do payroll better" is not actionable

**Three-Dimension Justification:**
- **Reader value:** Helpful payroll tips
- **Business value:** Shows expertise
- **Landscape value:** Lots of articles about this already but we can make it better

❌ **Why this fails:**
- Reader value is generic
- Business value doesn't explain conversion path
- Landscape value admits content already exists but doesn't explain differentiation

**Information Gain:**
We'll provide comprehensive tips about payroll.

❌ **Why this fails:** No specific unique contribution identified. "Comprehensive" is now the baseline, not the differentiator.

### Information Gain Verification

**1. Unique Contribution Test:**
- Contribution 1: Tips that help small businesses
- Contribution 2: Easy to understand advice
- Contribution 3: Practical information

❌ **KILL SWITCH TRIGGERED:** Cannot identify 3 specific things this piece adds beyond existing SERP results. This brief should NOT proceed to writing.

### Quality Cliff Assessment

- **Topic difficulty:** High cliff (extremely competitive keyword)
- **Mandatory differentiator:** [None identified]

❌ **Why this fails:** Competing on high-cliff topic without differentiation strategy

---

**What should have happened:**
This brief should be rejected and sent back with guidance:
1. "Payroll tips" is too broad — narrow to specific pain point
2. Information gain is not articulated — identify what's missing from SERP
3. No proprietary data or unique angle identified
4. Recommend reframing: "5 Payroll Mistakes First-Time Employers Make (And How to Avoid Them)" with Paychex data
```

---

### Example_Outline_Strong.md

```markdown
---
Document: Example_Outline_Strong
Category: Examples
Topics: outline, content structure, BLUF
Purpose: Few-shot example of excellent outline structure
Last Updated: 2026-02-05
---

## Example: Strong Content Outline

### Document Info
- **Brief Title:** "When Salaried Employees Qualify for Overtime (And How to Calculate It)"
- **Target Keyword:** how to calculate overtime pay for salaried employees
- **Word Count Target:** 1,500
- **Outline Word Estimate:** Intro (150) + 6 sections (~200 each) + FAQ (150) + Conclusion (100) = 1,500

### Proposed Structure

**Hook/Intro** (~150 words)
- Opening angle: "You hired your first salaried employee to simplify payroll. No more tracking hours, right? Not quite."
- Bridge to thesis: Common misconception that salary = no overtime
- Thesis statement: Paying someone a salary doesn't automatically make them exempt from overtime — here's how to know if you owe overtime and how to calculate it correctly.
- Reader promise: By the end, you'll know the three-part test, calculate overtime correctly, and avoid the costly mistake 30% of small businesses make.

---

**H2: The Costly Assumption Small Business Owners Make** (~200 words)

*Purpose:* Lead with the pain point and stakes

- **BLUF:** Assuming salaried = exempt from overtime is the #1 payroll mistake costing small businesses an average of $8,000 in back pay and penalties.

- Key point: Real DOL case example — small business penalized for misclassifying office manager
- Key point: Paychex data — "30% of businesses with <10 employees have at least one misclassified worker"
- Key point: Why this happens — the word "salary" sounds official and exempt-like

*Transition:* So what actually determines whether a salaried employee is exempt? Three tests.

---

**H2: The Three-Part Test for Overtime Exemption** (~200 words)

*Purpose:* Explain FLSA rules simply and clearly

- **BLUF:** To be exempt from overtime, an employee must pass ALL three tests: salary basis, salary level, and duties test. Fail one = owe overtime.

- H3: Salary Basis Test
  - Key point: Paid predetermined amount each week
  - Key point: Can't dock pay for partial-day absences (with exceptions)

- H3: Salary Level Test
  - Key point: Must earn at least $844/week ($43,888/year) as of July 2024
  - Key point: This threshold changes — check current DOL guidance

- H3: Duties Test (The Tricky One)
  - Key point: Job title doesn't matter — actual work duties determine status
  - Key point: Must perform exempt duties as primary job function
  - Example: "Office Manager" title doesn't automatically = administratively exempt

*Transition:* Let's look at specific job roles to see how this plays out.

---

**H2: Common Job Roles and Their Overtime Status** (~200 words)

*Purpose:* Give concrete examples readers can map to their situation

- **BLUF:** Here's how exemption applies to roles common in small businesses — with the duties test as the deciding factor.

- H3: Usually Non-Exempt (Owe Overtime)
  - Office assistant/administrative assistant — primarily clerical work
  - Bookkeeper — unless managing accounting function for business
  - Project coordinator — coordination ≠ management

- H3: Usually Exempt (No Overtime)
  - Operations manager — true management duties + supervision authority
  - Sales manager — if meets outside sales or administrative exemption
  - IT manager — if managing systems/infrastructure, not just help desk

- H3: It Depends (Analyze Actual Duties)
  - "Manager" titles that don't actually manage people
  - "Administrative" roles that are really clerical
  - "Professional" roles that don't require advanced degree

*Transition:* If your salaried employee doesn't meet all three tests, here's how to calculate their overtime.

---

**H2: How to Calculate Overtime for Non-Exempt Salaried Employees** (~250 words)

*Purpose:* Step-by-step calculation with example

- **BLUF:** Calculate the regular rate by dividing weekly salary by hours salary is intended to compensate, then multiply by 1.5 for overtime hours.

- Step 1: Determine the regular rate
  - Formula: Weekly salary ÷ hours salary is intended to cover = regular rate
  - Example: $800/week salary ÷ 40 hours = $20/hour regular rate

- Step 2: Calculate overtime rate
  - Formula: Regular rate × 1.5 = overtime rate
  - Example: $20 × 1.5 = $30/hour overtime rate

- Step 3: Calculate overtime pay for the week
  - Formula: Overtime hours × overtime rate = additional pay owed
  - Example: 5 overtime hours × $30 = $150 additional (on top of $800 salary)

- H3: Full Example Walkthrough
  - Employee: Office assistant, salaried at $800/week
  - Week scenario: Works 45 hours
  - Calculation: $800 base + (5 OT hours × $30) = $950 total pay

*Transition:* [PRODUCT INTEGRATION] This is why SurePayroll automatically handles these calculations.

---

**H2: How SurePayroll Handles This Automatically** (~150 words)

*Purpose:* Natural product integration solving the complexity just demonstrated

- **BLUF:** SurePayroll automatically determines exempt status during employee setup and calculates overtime when a non-exempt salaried employee exceeds 40 hours.

- Connection to earlier content: Remember that three-part test? SurePayroll asks the questions needed to assess exemption status.
- Feature highlight: During employee setup, system guides you through duties test questions
- Feature highlight: If employee is non-exempt salaried, system automatically calculates overtime using the formula above
- Proof point: "We've processed overtime for 500,000+ salaried non-exempt employees"
- Natural next step: "See how it works" [CTA]

*Transition:* What if you realize you've been miscategorizing someone?

---

**H2: How to Fix Misclassification** (~150 words)

*Purpose:* Answer the follow-up question they're now asking

- **BLUF:** If you discover you've misclassified an employee, calculate and pay back overtime owed, update their status going forward, and document the correction.

- Key point: Calculate back pay for up to 2 years (3 if willful violation)
- Key point: Update payroll system to non-exempt status immediately
- Key point: Communicate change to employee professionally
- Key point: Consult employment attorney if significant back pay owed
- Key point: DOL self-audit programs exist — voluntary correction has lower penalties

---

**H2: FAQ / Edge Cases** (~150 words)

*Purpose:* Answer the question they didn't know to ask (CC7)

**Q: Can I switch an employee between salaried and hourly?**
A: Yes, but the change must be communicated in advance and can't be retroactive. Switching to avoid overtime is legal if done prospectively, but audit your reasoning.

**Q: What about fluctuating workweek method?**
A: Some employers use FWW for non-exempt salaried employees, but it requires written agreement and is complex. Not recommended for first-time employers.

**Q: Does the salary threshold apply to all exemptions?**
A: No — outside sales, teachers, doctors, and lawyers have different rules. This guide focuses on administrative/executive exemptions most relevant to small businesses.

---

**Conclusion** (~100 words)
- Recap: Salary doesn't equal exempt — you need to pass the three-part test, especially duties
- Action step: Review your salaried employees' actual job duties to verify exemption status
- CTA: "Not sure where your employees fall? SurePayroll's setup wizard guides you through the determination. Try it free."

---

### Outline Self-Check
✅ Every H2 could be searched as its own query
✅ Skimming headers gives the full story
✅ BLUF applied — answers before explanations
✅ Product integration appears naturally in "How to calculate" section (after showing complexity)
✅ "Question they didn't know to ask" addressed in FAQ (fixing misclassification)
✅ Word count allocations sum to ~1,500
✅ No section requires another section to make sense (each H2 standalone)

### Notes for Draft Stage
- Need current 2026 salary threshold from DOL
- Verify Paychex stat: "30% of <10 employee businesses have misclassified worker"
- Get real DOL penalty case example for opening
```

---

## File Naming Convention

Use this consistent pattern:

```
SurePayroll_[Category]_[DocumentName].md
```

Examples:
- `SurePayroll_Core_ContentCode.md`
- `SurePayroll_Core_VoiceTone.md`
- `SurePayroll_Example_BriefStrong.md`
- `SurePayroll_Research_DeepSynthesis.md`

---

## Maintenance Schedule

| Action | Frequency | Owner |
|--------|-----------|-------|
| Verify character counts | Monthly | Content Ops |
| Update examples with latest best practices | Quarterly | Content Lead |
| Audit metadata tags | Quarterly | Content Ops |
| Review retrieval performance | Monthly | System Admin |
| Update document summaries | When content changes | Document Owner |

---

## Next Steps

1. Create SharePoint site: "SurePayroll Content System"
2. Upload existing 11 documents with new headers
3. Create 5 example files (strong/weak briefs, strong outline, strong draft, strong review)
4. Configure managed metadata
5. Add document properties
6. Test retrieval with sample queries

---

## Verification Commands

After setup, test retrieval with these queries in Copilot:
- "What are the 7 Content Code principles?"
- "Show me an example of a strong brief"
- "What is CC1 and when does content violate it?"
- "How should I structure an outline?"
