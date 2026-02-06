# Implementation Evaluation Rubric

## Purpose

This rubric allows you (or another evaluator) to assess the quality, completeness, and correctness of this Copilot Studio implementation. Use this to find gaps, mistakes, or improvement opportunities.

**How to Use:**
1. Review each criterion
2. Score 1-5 based on evidence
3. Note specific gaps or issues found
4. Prioritize improvements based on impact

---

## Scoring Scale

| Score | Meaning | Description |
|-------|---------|-------------|
| **5** | Excellent | Exceeds requirements, no improvements needed |
| **4** | Good | Meets requirements well, minor improvements possible |
| **3** | Adequate | Meets basic requirements, noticeable gaps |
| **2** | Poor | Significant gaps, requires major rework |
| **1** | Unacceptable | Fails to meet requirements, unusable |

---

## Evaluation Dimensions

### A. Requirements Alignment (Weight: 25%)

#### A1: User Requirements Met

**Criterion:** Does this implementation deliver what the user requested?

**User Requirements Checklist:**
- [ ] Agent works in Copilot Studio (not generic ChatGPT)
- [ ] Uses RAG with SharePoint documents as grounding
- [ ] Covers all 7 workflow stages (Brief → Quality Gate)
- [ ] Feels like "custom GPT" (conversational, not form-filling)
- [ ] Writer doesn't need to copy/paste prompts
- [ ] Can progress through stages conversationally
- [ ] Built-in prompts call on documentation automatically

**Evidence to Check:**
- Review `02_Agent_System_Instructions.md` - Does it reference SharePoint?
- Review `03_Agent_Topics_Configuration.md` - Are all 7 stages covered?
- Check if topics have conversational triggers (not rigid forms)
- Verify instructions are embedded in topics (not requiring manual paste)

**Score: _____ / 5**

**Gaps Found:**
-
-
-

**Improvement Recommendations:**
-
-

---

#### A2: Research Synthesis Applied

**Criterion:** Were the 38 improvements from Deep Research Synthesis incorporated?

**Key Improvements to Verify:**

| Improvement | Applied? | Evidence | Notes |
|-------------|----------|----------|-------|
| Information Gain mandatory | ✅/❌ | Check Brief topic includes IG verification | |
| Prompts under 500 words | ✅/❌ | Measure topic instructions length | |
| 2-3 few-shot examples | ✅/❌ | Check for Example_Brief_Strong.md | |
| Brief is leverage point (3x detail) | ✅/❌ | Compare Brief topic length to others | |
| Kill switch for weak topics | ✅/❌ | Check Brief topic instructions | |
| Layered credibility (Paychex first) | ✅/❌ | Check Draft topic instructions | |
| Quality Cliff assessment | ✅/❌ | Check Brief topic for cliff assessment | |
| Graceful degradation | ✅/❌ | Check all topics for fallback handling | |
| SharePoint 36k char limit addressed | ✅/❌ | Check SharePoint structure doc | |

**Score: _____ / 5**

**Gaps Found:**
-
-

**Evidence:**
-

---

#### A3: Microsoft Best Practices Followed

**Criterion:** Does this follow Copilot Studio documentation and best practices?

**Best Practices Checklist:**

| Practice | Applied? | Evidence Location | Notes |
|----------|----------|-------------------|-------|
| Generative orchestration enabled | ✅/❌ | Deployment guide Phase 2.5 | |
| Topics have high-quality descriptions | ✅/❌ | Each topic in 03_Agent_Topics | |
| Limit to 25-30 topics (we have 7) | ✅/❌ | Topic count | |
| Numbered/listed instructions | ✅/❌ | Topic instructions format | |
| Semantic search enabled | ✅/❌ | Deployment guide Phase 2.4 | |
| SharePoint metadata configured | ✅/❌ | SharePoint structure doc | |
| Knowledge source limits respected | ✅/❌ | Check file sizes < 36k chars | |

**Score: _____ / 5**

**Gaps Found:**
-
-

**Citations:**
Review against:
- [Generative Orchestration Guide](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/generative-orchestration)
- [Knowledge Sources Summary](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-copilot-studio)

---

### B. Technical Quality (Weight: 25%)

#### B1: SharePoint Structure

**Criterion:** Is the SharePoint structure optimized for RAG retrieval?

**Checklist:**

| Element | Implemented? | Quality | Notes |
|---------|-------------|---------|-------|
| Folder structure logical | ✅/❌ | 1-5 | |
| Documents under 36k chars | ✅/❌ | 1-5 | Did they verify this? |
| Metadata schema defined | ✅/❌ | 1-5 | |
| Document headers for retrieval | ✅/❌ | 1-5 | |
| Examples included (Strong/Weak) | ✅/❌ | 1-5 | |
| Naming convention consistent | ✅/❌ | 1-5 | |
| Summary sections in each doc | ✅/❌ | 1-5 | |

**Test:**
1. Check `01_SharePoint_Structure.md` for completeness
2. Verify document header template includes all necessary metadata
3. Check if example files are actually created (not just spec'd)

**Score: _____ / 5**

**Issues Found:**
-
-

---

#### B2: System Instructions Quality

**Criterion:** Are system instructions comprehensive, clear, and correct?

**Checklist:**

| Element | Present? | Quality | Evidence |
|---------|----------|---------|----------|
| Role definition clear | ✅/❌ | 1-5 | Intro paragraph |
| Core purpose stated | ✅/❌ | 1-5 | "You guide writers through 7 stages..." |
| Critical rules enumerated | ✅/❌ | 1-5 | 6 numbered rules |
| Information Gain emphasized | ✅/❌ | 1-5 | Rule #1 |
| Voice rules embedded | ✅/❌ | 1-5 | Rule #3 |
| SharePoint fallback handling | ✅/❌ | 1-5 | Rule #4 |
| Conversation state management | ✅/❌ | 1-5 | "Track these details..." |
| Response format examples | ✅/❌ | 1-5 | Brief/Review format blocks |
| Tone guidance | ✅/❌ | 1-5 | "Direct and efficient..." |

**Test:**
1. Read `02_Agent_System_Instructions.md` end-to-end
2. Check for contradictions or ambiguity
3. Verify all voice rules from Voice_Tone.md are included
4. Check if examples are concrete (not vague)

**Potential Issues to Check:**
- Are instructions too long? (research says <500 words, but system instructions may be exception)
- Any contradictory guidance?
- Missing critical rules from Content_Code.md?

**Score: _____ / 5**

**Issues Found:**
-
-

---

#### B3: Topic Configuration Quality

**Criterion:** Are topics well-designed for their purpose?

**For EACH of 7 topics, evaluate:**

| Topic | Description Quality (1-5) | Trigger Phrases (1-5) | Instructions Clarity (1-5) | Length (<500 words?) | Overall Score |
|-------|---------------------------|----------------------|---------------------------|---------------------|---------------|
| 1. Brief Generation | | | | | |
| 2. Outline Creation | | | | | |
| 3. First Draft | | | | | |
| 4. Editorial Review | | | | | |
| 5. Writer Revision | | | | | |
| 6. Final Polish | | | | | |
| 7. Quality Gate | | | | | |

**Deep Dive Checks:**

**Topic 1 (Brief Generation):**
- [ ] Information Gain verification section present?
- [ ] Quality Cliff assessment included?
- [ ] Kill switch mechanism clear?
- [ ] Example reference (Example_Brief_Strong.md)?

**Topic 3 (First Draft):**
- [ ] Voice substitution table referenced?
- [ ] Credibility layering (CC6) explained?
- [ ] Grammar rules embedded?
- [ ] Product integration guidance?

**Topic 4 (Editorial Review):**
- [ ] All 7 CC principles checked?
- [ ] 10-point scoring explained?
- [ ] Voice violation detection?
- [ ] Priority ranking of fixes?

**Overall Topic Score: _____ / 5**

**Issues Found:**
-
-

---

#### B4: Deployment Guide Completeness

**Criterion:** Can someone follow this guide and successfully deploy the agent?

**Checklist:**

| Section | Complete? | Quality | Testability |
|---------|-----------|---------|-------------|
| SharePoint setup steps | ✅/❌ | 1-5 | Can you follow it? |
| Agent creation steps | ✅/❌ | 1-5 | Step-by-step clear? |
| System instruction config | ✅/❌ | 1-5 | Copy/paste ready? |
| Knowledge source setup | ✅/❌ | 1-5 | Correct settings? |
| Topic creation (7 topics) | ✅/❌ | 1-5 | Repeatable process? |
| Testing validation | ✅/❌ | 1-5 | Pass/fail criteria? |
| Troubleshooting guide | ✅/❌ | 1-5 | Common issues covered? |
| Maintenance schedule | ✅/❌ | 1-5 | Ongoing ops defined? |

**Test:**
1. Pick a random step from the deployment guide
2. Check if it has: what to do, where to do it, expected outcome
3. Verify screenshots or precise navigation instructions

**Missing Elements Check:**
- Are there steps that assume knowledge not provided?
- Any "do X" without explaining HOW to do X?
- Missing verification steps?

**Score: _____ / 5**

**Gaps Found:**
-
-

---

### C. Content Quality (Weight: 20%)

#### C1: Documentation Clarity

**Criterion:** Are the documents well-written, clear, and actionable?

**Evaluate each document:**

| Document | Clarity (1-5) | Completeness (1-5) | Actionable (1-5) | Errors/Typos |
|----------|---------------|-------------------|-----------------|--------------|
| 01_SharePoint_Structure | | | | |
| 02_Agent_System_Instructions | | | | |
| 03_Agent_Topics_Configuration | | | | |
| 04_Deployment_Guide | | | | |
| 05_Testing_Framework | | | | |
| 06_Implementation_Evaluation_Rubric | | | | |

**Criteria:**
- **Clarity:** Easy to understand, no jargon without explanation
- **Completeness:** All necessary information present
- **Actionable:** Clear next steps, can execute without guessing
- **Errors:** Typos, broken formatting, incorrect references

**Score: _____ / 5**

**Issues:**
-
-

---

#### C2: Example Quality

**Criterion:** Are examples helpful, realistic, and instructive?

**Examples to Evaluate:**

| Example | Purpose Clear? | Realistic? | Shows Anti-pattern? | Annotations Helpful? |
|---------|---------------|-----------|-------------------|---------------------|
| Example_Brief_Strong.md | ✅/❌ | ✅/❌ | N/A | ✅/❌ |
| Example_Brief_Weak.md | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Example_Outline_Strong.md | ✅/❌ | ✅/❌ | N/A | ✅/❌ |

**Test:**
- Would a writer understand WHY the strong example is strong?
- Would they recognize the weak example's flaws?
- Are examples complete enough to use as templates?

**Score: _____ / 5**

**Improvements Needed:**
-
-

---

### D. Completeness & Coverage (Weight: 15%)

#### D1: Workflow Coverage

**Criterion:** Are all workflow stages adequately covered?

| Stage | Topic Exists? | Instructions Complete? | Examples Present? | Gap Analysis |
|-------|--------------|----------------------|------------------|--------------|
| Briefing | ✅/❌ | ✅/❌ | ✅/❌ | |
| Outline | ✅/❌ | ✅/❌ | ✅/❌ | |
| First Draft | ✅/❌ | ✅/❌ | ✅/❌ | |
| Editorial Review | ✅/❌ | ✅/❌ | ✅/❌ | |
| Writer Revision | ✅/❌ | ✅/❌ | ✅/❌ | |
| Final Polish | ✅/❌ | ✅/❌ | ✅/❌ | |
| Quality Gate | ✅/❌ | ✅/❌ | ✅/❌ | |

**Missing Workflows:**
- Content refresh/updating existing content?
- Content deletion/retirement decisions?
- Emergency fixes for published content?

**Score: _____ / 5**

**Gaps:**
-
-

---

#### D2: Documentation Coverage

**Criterion:** Are all 11 original docs integrated into the system?

| Original Document | Referenced in Topics? | Header Added? | Examples Use It? | Metadata Set? |
|-------------------|---------------------|---------------|-----------------|---------------|
| CONTEXT.md | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Content_Code.md | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Voice_Tone.md | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Grammar_Mechanics.md | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Inclusion_Accessibility.md | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Positioning.md | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Features_Benefits.md | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Quality_Standards.md | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Workflow_Stages.md | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| ICP_Personas.md | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Content_Brief_Template.md | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |

**Test:**
Search all topic instructions for references to each doc. Are they actually used or just mentioned?

**Score: _____ / 5**

**Unused Documents:**
-
-

---

### E. Testability & Validation (Weight: 15%)

#### E1: Testing Framework Quality

**Criterion:** Can the agent be properly tested using the provided framework?

**Checklist:**

| Test Type | Present? | Comprehensive? | Executable? | Pass Criteria Clear? |
|-----------|----------|---------------|-------------|---------------------|
| Unit tests (topics) | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Unit tests (retrieval) | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Unit tests (voice) | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Stress tests (volume) | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Stress tests (edge cases) | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| 20x consistency test | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |

**Coverage Analysis:**
- Are critical paths tested?
- Are failure modes tested?
- Can tests be automated?

**Score: _____ / 5**

**Missing Tests:**
-
-

---

#### E2: Success Metrics Defined

**Criterion:** Are there clear metrics to measure if this is working?

**Metrics Checklist:**

| Metric Category | Defined? | Measurable? | Baselines Set? | Targets Set? |
|----------------|----------|-------------|---------------|--------------|
| Process metrics | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Quality metrics | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Efficiency metrics | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |
| Usage metrics | ✅/❌ | ✅/❌ | ✅/❌ | ✅/❌ |

**Key Metrics from Deployment Guide:**
- Average quality score at Final Polish (target: 7+)
- % passing Quality Gate first time (target: 80%+)
- Time from Brief to Published (target: <5 days)

**Are these realistic? Actionable? Will they drive improvement?**

**Score: _____ / 5**

**Metric Gaps:**
-
-

---

## Critical Flaws Check

### Blocking Issues (Any one fails = implementation unusable)

| Critical Requirement | Met? | Evidence | If Not Met, Impact |
|---------------------|------|----------|-------------------|
| SharePoint RAG actually works | ✅/❌ | Test with deployment | Agent can't ground in docs |
| Topics route correctly | ✅/❌ | Test all 7 trigger phrases | Writer can't access stages |
| Voice rules enforced | ✅/❌ | Test voice violation detection | Output doesn't match brand |
| Information Gain required | ✅/❌ | Test brief generation | Weak content gets approved |
| Compliance checks work | ✅/❌ | Test final polish | Legal/regulatory risk |
| Quality Gate makes decisions | ✅/❌ | Test pass/fail logic | No clear approval process |

**Critical Flaws Found:**
-
-

**Remediation Required:**
-
-

---

## Error Analysis

### Common Implementation Mistakes to Check

#### Mistake 1: Overly Long Prompts

**Check:** Measure topic instruction word counts
**Research Finding:** Prompts should be <500 words for optimal attention
**Actual Lengths:**
- Topic 1 (Brief): _____ words
- Topic 2 (Outline): _____ words
- Topic 3 (Draft): _____ words
- Topic 4 (Review): _____ words
- Topic 5 (Revision): _____ words
- Topic 6 (Polish): _____ words
- Topic 7 (Gate): _____ words

**Issue?** ✅ All <500 words / ❌ Some exceed limit

**Fix:**
-

---

#### Mistake 2: Self-Verification Unreliability

**Check:** Do any topics ask the agent to self-verify?
**Research Finding:** LLMs confabulate compliance - need separate evaluation

**Found in:**
-
-

**Issue?** ✅ No self-verification / ❌ Self-verification present

**Fix:**
-

---

#### Mistake 3: Missing Few-Shot Examples

**Check:** Are 2-3 examples provided for critical stages?
**Research Finding:** Examples dramatically improve quality

**Examples Present:**
- Brief: ✅ Strong / ✅ Weak / ❌ Missing
- Outline: ✅ Strong / ❌ Weak / ❌ Missing
- Draft: ✅ Strong / ❌ Weak / ❌ Missing
- Review: ✅ Strong / ❌ Weak / ❌ Missing

**Issue?** ✅ Sufficient examples / ❌ Missing critical examples

**Fix:**
-

---

#### Mistake 4: Weak Topic Descriptions

**Check:** Are topic descriptions specific enough for AI routing?
**Best Practice:** Descriptions should explain what the topic does and when to use it

**Review each topic description:**
- Topic 1: Clear? ✅/❌ Specific? ✅/❌
- Topic 2: Clear? ✅/❌ Specific? ✅/❌
- Topic 3: Clear? ✅/❌ Specific? ✅/❌
- Topic 4: Clear? ✅/❌ Specific? ✅/❌
- Topic 5: Clear? ✅/❌ Specific? ✅/❌
- Topic 6: Clear? ✅/❌ Specific? ✅/❌
- Topic 7: Clear? ✅/❌ Specific? ✅/❌

**Issue?** ✅ All clear / ❌ Some vague

**Fix:**
-

---

#### Mistake 5: SharePoint File Size Violations

**Check:** Are any docs over 36,000 character limit?
**Technical Limit:** Copilot Studio can't index files >36k chars

**Document Sizes:**
(Would need to measure actual files)
- Content_Code.md: _____ chars
- Voice_Tone.md: _____ chars
- [etc...]

**Issue?** ✅ All under limit / ❌ Some exceed

**Fix:**
-

---

## Overall Assessment

### Dimension Scores Summary

| Dimension | Weight | Score (1-5) | Weighted Score |
|-----------|--------|-------------|----------------|
| A. Requirements Alignment | 25% | _____ | _____ |
| B. Technical Quality | 25% | _____ | _____ |
| C. Content Quality | 20% | _____ | _____ |
| D. Completeness & Coverage | 15% | _____ | _____ |
| E. Testability & Validation | 15% | _____ | _____ |
| **TOTAL** | **100%** | | **_____ / 5.0** |

---

### Final Recommendation

#### If Score ≥ 4.0: **APPROVE**
- Implementation is production-ready
- Proceed with deployment
- Address minor improvements in post-launch iteration

#### If Score 3.0-3.9: **CONDITIONAL APPROVAL**
- Implementation is functional but has gaps
- Address priority issues before launch
- Plan fixes in sprint 1 post-launch

#### If Score < 3.0: **REJECT**
- Significant issues require resolution
- Not ready for production deployment
- Prioritize fixes and re-evaluate

**My Recommendation: _____**

**Rationale:**
-
-
-

---

## Top 10 Priority Improvements

Based on evaluation, list improvements in priority order:

1. **[Improvement]** - Impact: High/Medium/Low - Effort: High/Medium/Low
2. **[Improvement]** - Impact: ___ - Effort: ___
3. **[Improvement]** - Impact: ___ - Effort: ___
4. **[Improvement]** - Impact: ___ - Effort: ___
5. **[Improvement]** - Impact: ___ - Effort: ___
6. **[Improvement]** - Impact: ___ - Effort: ___
7. **[Improvement]** - Impact: ___ - Effort: ___
8. **[Improvement]** - Impact: ___ - Effort: ___
9. **[Improvement]** - Impact: ___ - Effort: ___
10. **[Improvement]** - Impact: ___ - Effort: ___

---

## Evaluator Information

**Evaluator Name:** _____________________
**Date of Evaluation:** _____________________
**Evaluation Duration:** _____ hours
**Evaluation Method:**
- [ ] Document review only
- [ ] Document review + deployment test
- [ ] Document review + deployment + user testing

**Expertise Level:**
- [ ] Copilot Studio expert
- [ ] Content operations expert
- [ ] SurePayroll domain expert
- [ ] Independent technical reviewer

**Bias Declaration:**
- [ ] No conflict of interest
- [ ] [Describe any potential biases]

---

## Appendix: Detailed Findings

Use this section for detailed notes, screenshots, or specific examples of issues found.

### Finding 1: [Title]
**Category:** [Technical / Content / Process]
**Severity:** [Critical / High / Medium / Low]
**Description:**
[Detailed description of issue]

**Evidence:**
[Quotes, screenshots, specific line numbers]

**Recommendation:**
[How to fix]

**Impact if Not Fixed:**
[What could go wrong]

---

### Finding 2: [Title]
[Repeat format...]

---

## Sign-Off

**Evaluator Signature:** _____________________
**Date:** _____________________

**Evaluation Status:**
- [ ] ✅ APPROVED - Ready for production
- [ ] ⚠️ CONDITIONAL - Fix priority issues first
- [ ] ❌ REJECTED - Significant rework required

---

**End of Evaluation Rubric**

Use this rubric to conduct a thorough, objective assessment of the implementation quality.
