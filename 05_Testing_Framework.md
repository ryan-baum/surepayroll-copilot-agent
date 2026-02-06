# Testing & Stress Testing Framework

## Overview

This framework provides unit tests and stress tests to validate the SurePayroll Content Agent performs correctly under normal and extreme conditions.

---

## Unit Testing Protocol

### Unit Test Suite: Topic Activation

**Purpose:** Verify each topic triggers correctly with expected inputs

#### Test 1.1: Brief Generation Topic

**Test Cases:**

| Test ID | Input Query | Expected Topic | Expected Behavior | Pass/Fail |
|---------|-------------|----------------|-------------------|-----------|
| UT-1.1a | "Create a brief for payroll tax deadlines" | Brief Generation | Retrieves Content_Code.md, generates brief with IG section | |
| UT-1.1b | "Plan content about overtime pay" | Brief Generation | Retrieves docs, assesses quality cliff | |
| UT-1.1c | "Generate content brief" | Brief Generation | Asks for topic if not specified | |
| UT-1.1d | "Brief for [extremely niche topic]" | Brief Generation | Triggers kill switch if no IG possible | |
| UT-1.1e | "Create brief for [vague topic like 'payroll tips']" | Brief Generation | Recommends reframing with specific angle | |

**Validation Criteria:**
- ✅ Topic activates correctly
- ✅ Retrieves at minimum: Content_Code.md, Positioning.md
- ✅ Information Gain section present with 3 specific contributions
- ✅ Quality Cliff assessment included
- ✅ Kill switch triggers when IG can't be articulated

---

#### Test 1.2: Outline Creation Topic

**Test Cases:**

| Test ID | Input Query | Expected Topic | Expected Behavior | Pass/Fail |
|---------|-------------|----------------|-------------------|-----------|
| UT-1.2a | "Create outline from this brief" | Outline Creation | Retrieves Example_Outline_Strong.md, applies BLUF | |
| UT-1.2b | "Structure this content" | Outline Creation | Generates H2/H3 structure | |
| UT-1.2c | "Outline for [topic]" without brief | Outline Creation | Requests brief first OR creates from scratch | |
| UT-1.2d | [Paste brief with weak IG] "Create outline" | Outline Creation | Flags IG weakness before proceeding | |

**Validation Criteria:**
- ✅ BLUF applied to each section (answer before explanation)
- ✅ H2s work as standalone questions
- ✅ Product integration point identified (not tacked on)
- ✅ CC7 section present (anticipates next question)
- ✅ Word count allocation sums to target

---

#### Test 1.3: First Draft Topic

**Test Cases:**

| Test ID | Input Query | Expected Topic | Expected Behavior | Pass/Fail |
|---------|-------------|----------------|-------------------|-----------|
| UT-1.3a | "Write first draft from outline" | First Draft Writing | Retrieves Voice_Tone.md, applies substitution table | |
| UT-1.3b | "Draft this content" | First Draft Writing | No exclamation points in output | |
| UT-1.3c | "Create draft" | First Draft Writing | Applies grammar rules (Oxford comma, em dash with spaces) | |
| UT-1.3d | "Write article about [topic]" | First Draft Writing | Layers credibility (Paychex first) | |

**Validation Criteria:**
- ✅ Zero exclamation points
- ✅ Zero instances of "we're excited" or similar
- ✅ Zero instances of "you might want to consider"
- ✅ Product integration natural (not forced)
- ✅ Meta title under 60 chars, meta description under 155 chars
- ✅ BLUF structure in every section

---

#### Test 1.4: Editorial Review Topic

**Test Cases:**

| Test ID | Input Query | Expected Topic | Expected Behavior | Pass/Fail |
|---------|-------------|----------------|-------------------|-----------|
| UT-1.4a | "Review this draft" [paste draft] | Editorial Review | Checks all 7 CC principles | |
| UT-1.4b | "Evaluate this content" [draft with exclamations] | Editorial Review | Flags all exclamation points | |
| UT-1.4c | "Score this draft" [high-quality draft] | Editorial Review | Scores 7+ with justification | |
| UT-1.4d | "Review for voice" [draft with hedging] | Editorial Review | Identifies all hedging instances | |

**Validation Criteria:**
- ✅ All 7 CC principles evaluated (CC1-CC7)
- ✅ Score provided (1-10) with specific evidence
- ✅ Voice violations quoted with exact fixes
- ✅ Priority fixes ranked in order
- ✅ Recommendation clear (approve/return/escalate)

---

#### Test 1.5: Writer Revision Topic

**Test Cases:**

| Test ID | Input Query | Expected Topic | Expected Behavior | Pass/Fail |
|---------|-------------|----------------|-------------------|-----------|
| UT-1.5a | "Help me revise this draft" | Writer Revision | Guides through priority fixes first | |
| UT-1.5b | "Apply this feedback" [with pattern fixes] | Writer Revision | Applies pattern throughout, not just flagged instances | |
| UT-1.5c | "How do I fix these issues?" | Writer Revision | Provides before/after examples | |

**Validation Criteria:**
- ✅ Priority fixes addressed in order
- ✅ Pattern fixes applied throughout
- ✅ Revision log documents changes
- ✅ Voice consistent after revisions

---

#### Test 1.6: Final Polish Topic

**Test Cases:**

| Test ID | Input Query | Expected Topic | Expected Behavior | Pass/Fail |
|---------|-------------|----------------|-------------------|-----------|
| UT-1.6a | "Final compliance check" | Final Polish | Verifies no "guarantee" language | |
| UT-1.6b | "Line edit this content" | Final Polish | Checks grammar (Oxford comma, em dash, etc.) | |
| UT-1.6c | "Pre-publication review" [draft with compliance issues] | Final Polish | Flags all compliance violations | |

**Validation Criteria:**
- ✅ Compliance checklist completed (6 items)
- ✅ No "guarantee" language
- ✅ No absolute compliance claims
- ✅ Grammar verified (all rules from Grammar_Mechanics.md)
- ✅ Inclusion check applied

---

#### Test 1.7: Quality Gate Topic

**Test Cases:**

| Test ID | Input Query | Expected Topic | Expected Behavior | Pass/Fail |
|---------|-------------|----------------|-------------------|-----------|
| UT-1.7a | "Is this ready to publish?" [passing draft] | Quality Gate | Returns ✅ PASS with rationale | |
| UT-1.7b | "Final quality check" [failing draft] | Quality Gate | Returns ❌ FAIL with specific issues | |
| UT-1.7c | "Quality gate review" [borderline draft] | Quality Gate | Makes decisive call (not "maybe") | |

**Validation Criteria:**
- ✅ Binary decision (PASS or FAIL, no "maybe")
- ✅ All 7 CC principles checked
- ✅ Quality score estimated
- ✅ If FAIL, clear return path specified
- ✅ Rationale provided with evidence

---

## Unit Test Suite: Knowledge Retrieval

**Purpose:** Verify SharePoint documents are retrieved correctly

#### Test 2.1: Document Retrieval

| Test ID | Query | Expected Document | Retrieval Success | Pass/Fail |
|---------|-------|-------------------|-------------------|-----------|
| UT-2.1a | "What are the 7 Content Code principles?" | Content_Code.md | Retrieved and summarized | |
| UT-2.1b | "Show me voice guidelines" | Voice_Tone.md | Retrieved substitution table | |
| UT-2.1c | "What are grammar rules for em dashes?" | Grammar_Mechanics.md | Retrieved specific rule | |
| UT-2.1d | "Show me an example of a strong brief" | Example_Brief_Strong.md | Retrieved example | |
| UT-2.1e | "What is CC1?" | Content_Code.md | Retrieved specific section | |

**Validation Criteria:**
- ✅ Correct document retrieved
- ✅ Relevant section extracted
- ✅ Answer matches document content
- ✅ Graceful degradation if document not found

---

#### Test 2.2: Fallback Handling

| Test ID | Query | Expected Behavior | Pass/Fail |
|---------|-------|-------------------|-----------|
| UT-2.2a | "What does [NonexistentDoc].md say?" | States "Unable to retrieve [NonexistentDoc].md" | |
| UT-2.2b | Request specific doc that doesn't exist | Proceeds with general guidelines | |
| UT-2.2c | All SharePoint docs unavailable (simulated) | Flags for human review | |

**Validation Criteria:**
- ✅ Explicit statement of retrieval failure
- ✅ Proceeds with general principles
- ✅ Flags output for review
- ✅ No confabulation of missing content

---

## Unit Test Suite: Voice Compliance

**Purpose:** Verify voice rules are consistently applied

#### Test 3.1: Voice Violation Detection

| Test ID | Input Text | Expected Violations Flagged | Pass/Fail |
|---------|-----------|----------------------------|-----------|
| UT-3.1a | "We're so excited to announce!" | "We're excited" → violation | |
| UT-3.1b | "You might want to consider this option!" | "You might want to" + exclamation | |
| UT-3.1c | "It's important to note that..." | "It's important to note" → violation | |
| UT-3.1d | "Feel free to reach out anytime!" | "Feel free" + exclamation | |
| UT-3.1e | "Don't worry, we've got you covered!" | "Don't worry" + exclamation | |

**Validation Criteria:**
- ✅ All violations identified
- ✅ Specific rewrites provided
- ✅ Correct substitute suggested from Voice_Tone.md table

---

#### Test 3.2: Voice Generation

| Test ID | Generation Context | Expected Voice | Violations Found | Pass/Fail |
|---------|-------------------|----------------|------------------|-----------|
| UT-3.2a | Generate product announcement | Confident, direct, no exclamations | 0 violations | |
| UT-3.2b | Generate error message | Calm, solution-focused | 0 violations | |
| UT-3.2c | Generate onboarding content | Encouraging, not effusive | 0 violations | |

**Validation Criteria:**
- ✅ Zero exclamation points
- ✅ Zero banned phrases
- ✅ Confident tone throughout
- ✅ Practical and direct language

---

## Stress Testing Protocol

### Stress Test Suite: High Volume

**Purpose:** Test agent performance under heavy usage

#### Test ST-1: Concurrent Conversations

**Setup:**
- Simulate 10 simultaneous users
- Each running different workflow stages
- 30-minute test duration

**Metrics to Track:**

| Metric | Target | Actual | Pass/Fail |
|--------|--------|--------|-----------|
| Response time (average) | <5 seconds | | |
| Response time (p95) | <10 seconds | | |
| Error rate | <2% | | |
| Topic routing accuracy | >95% | | |
| Knowledge retrieval success | >90% | | |

**Test Scenarios:**
1. User A: Creating brief (10 queries)
2. User B: Writing draft (15 queries)
3. User C: Editorial review (8 queries)
4. User D: Revisions (12 queries)
5. User E: Voice questions (20 queries)
6. Users F-J: Mixed queries

**Pass Criteria:**
- ✅ All metrics meet targets
- ✅ No conversation context loss
- ✅ No incorrect topic routing
- ✅ Consistent voice across all responses

---

#### Test ST-2: Long Conversations

**Setup:**
- Single conversation with 100+ turns
- Full workflow: Brief → Outline → Draft → Review → Revision → Polish → Gate
- Multiple iterations and back-and-forth

**Metrics to Track:**

| Metric | Target | Actual | Pass/Fail |
|--------|--------|--------|-----------|
| Context retention | 100% through workflow | | |
| Response quality degradation | <10% by turn 100 | | |
| Token limit errors | 0 | | |
| Topic routing accuracy | >95% | | |

**Test Conversation Structure:**
1. Turns 1-15: Brief creation with iterations
2. Turns 16-25: Outline creation with refinements
3. Turns 26-50: Draft writing with section-by-section feedback
4. Turns 51-70: Editorial review with Q&A
5. Turns 71-85: Revisions with multiple rounds
6. Turns 86-95: Final polish with nitpicking
7. Turns 96-100: Quality gate and final questions

**Pass Criteria:**
- ✅ Agent remembers earlier stages
- ✅ Can reference "the brief we created" at turn 80
- ✅ Quality doesn't degrade
- ✅ No repetition or hallucination

---

### Stress Test Suite: Edge Cases

#### Test ST-3: Malformed Inputs

| Test ID | Input Type | Expected Behavior | Pass/Fail |
|---------|-----------|-------------------|-----------|
| ST-3.1 | Empty query | Prompts for clarification | |
| ST-3.2 | Extremely long paste (50,000 words) | Handles gracefully or requests chunking | |
| ST-3.3 | Special characters (#$%^&*) in topic | Processes correctly | |
| ST-3.4 | Multiple languages mixed | Responds in English, handles gracefully | |
| ST-3.5 | Code blocks in content | Formats correctly | |
| ST-3.6 | Very long file names/URLs | Handles without breaking | |

**Validation Criteria:**
- ✅ No system errors
- ✅ Graceful degradation
- ✅ Clear error messages if can't process
- ✅ Suggests alternative approach

---

#### Test ST-4: Knowledge Source Failures

**Setup:**
- Simulate SharePoint unavailable
- Test fallback behavior

| Scenario | Expected Behavior | Pass/Fail |
|----------|-------------------|-----------|
| All docs unavailable | States retrieval failure, proceeds with core principles | |
| Partial retrieval (3/11 docs) | Uses available docs, notes which are missing | |
| Retrieval timeout (>10 sec) | Falls back to general guidelines | |
| Doc corrupted/unreadable | Skips bad doc, uses others | |

**Validation Criteria:**
- ✅ Explicit acknowledgment of retrieval failure
- ✅ Proceeds without hallucinating content
- ✅ Flags for human review
- ✅ Quality degrades gracefully (not catastrophically)

---

#### Test ST-5: Contradictory Instructions

| Test ID | Scenario | Expected Behavior | Pass/Fail |
|---------|----------|-------------------|-----------|
| ST-5.1 | User says "use exclamation points" | Explains SurePayroll voice rules prohibit this | |
| ST-5.2 | User says "make it more exciting" | Interprets as "more engaging" while maintaining calm voice | |
| ST-5.3 | User requests generic content | Flags information gain requirement | |
| ST-5.4 | User wants to skip Brief stage | Explains why Brief is critical (60%+ of quality) | |

**Validation Criteria:**
- ✅ Agent respectfully pushes back
- ✅ Explains rationale from documentation
- ✅ Suggests compliant alternative
- ✅ Doesn't blindly follow bad instruction

---

### Stress Test Suite: Quality Consistency

#### Test ST-6: 20x Repetition Test

**Purpose:** Measure output variance and consistency (from research synthesis)

**Setup:**
Run the SAME query 20 times:

**Test Query:** "Review this draft for voice: 'We're so excited to announce our new feature! You might want to give it a try!'"

**Measure:**

| Metric | Target | Actual | Pass/Fail |
|--------|--------|--------|-----------|
| Violations identified (consistency) | 2 violations every time | | |
| Suggested rewrites (variance) | <20% variance in wording | | |
| Response structure (consistency) | Same format every time | | |
| Tone (consistency) | Professional tone every time | | |

**Acceptance Criteria:**
- ✅ <20% variance in core content
- ✅ 100% consistency in violations identified
- ✅ <10% variance in recommendations
- ✅ Zero hallucinations or errors

Repeat for:
- Brief generation (same topic)
- Outline creation (same brief)
- Quality scoring (same draft)

---

## Automated Testing Tools

### Test Harness Setup

**Create test script:**

```python
# test_copilot_agent.py
import requests
import json
from typing import List, Dict

class CopilotAgentTester:
    def __init__(self, agent_url: str, api_key: str):
        self.agent_url = agent_url
        self.api_key = api_key
        self.results = []

    def run_unit_test(self, test_id: str, query: str, expected_topic: str) -> Dict:
        """Run single unit test and record results"""
        response = self.send_query(query)
        result = {
            "test_id": test_id,
            "query": query,
            "expected_topic": expected_topic,
            "actual_topic": self.extract_topic(response),
            "passed": self.validate_response(response, expected_topic)
        }
        self.results.append(result)
        return result

    def run_stress_test(self, queries: List[str], concurrent: int = 10):
        """Run stress test with concurrent queries"""
        # Implementation for concurrent testing
        pass

    def run_20x_test(self, query: str) -> Dict:
        """Run same query 20 times and measure variance"""
        responses = [self.send_query(query) for _ in range(20)]
        variance = self.calculate_variance(responses)
        return {
            "query": query,
            "variance": variance,
            "passed": variance < 0.20  # <20% variance threshold
        }

    def generate_report(self) -> str:
        """Generate markdown test report"""
        pass_rate = sum(1 for r in self.results if r["passed"]) / len(self.results)
        return f"# Test Report\n\nPass Rate: {pass_rate:.1%}\n\n..."

# Usage
tester = CopilotAgentTester(agent_url="your-agent-url", api_key="your-key")
tester.run_unit_test("UT-1.1a", "Create a brief for payroll deadlines", "Brief Generation")
report = tester.generate_report()
```

---

## Testing Schedule

### Pre-Launch Testing (Before Phase 5 Deployment)

**Week 1:**
- ✅ All Unit Tests (Topics 1-7)
- ✅ Knowledge Retrieval Tests
- ✅ Voice Compliance Tests

**Week 2:**
- ✅ Stress Test: Concurrent Conversations
- ✅ Stress Test: Long Conversations
- ✅ Edge Case Tests

**Week 3:**
- ✅ 20x Repetition Tests (Brief, Outline, Review)
- ✅ Quality Consistency Tests
- ✅ Fix any failures

**Week 4:**
- ✅ Final validation
- ✅ User acceptance testing (2-3 writers)
- ✅ Go/No-Go decision

### Post-Launch Monitoring

**Daily (Week 1-2):**
- Check Analytics for errors
- Review failed conversations
- Quick fixes deployed

**Weekly (Month 1):**
- Run subset of unit tests (10 critical tests)
- Review quality metrics
- Update tests based on real usage

**Monthly (Ongoing):**
- Full unit test suite
- Selected stress tests
- 20x consistency test
- Update baselines

---

## Test Results Template

```markdown
# Test Results: [Date]

## Summary
- Tests Run: [X]
- Tests Passed: [X]
- Tests Failed: [X]
- Pass Rate: [XX%]

## Failed Tests

### Test ID: UT-1.1d
- **Expected:** Kill switch triggered for vague topic
- **Actual:** Generated brief anyway
- **Root Cause:** Information Gain check not strict enough
- **Fix Required:** Update Brief Generation topic instructions
- **Priority:** High

### Test ID: ST-3.2
- **Expected:** Handle 50,000 word paste gracefully
- **Actual:** Timeout error
- **Root Cause:** Token limit exceeded
- **Fix Required:** Add chunking guidance in system instructions
- **Priority:** Medium

## Recommendations
1. [Action item 1]
2. [Action item 2]
3. [Action item 3]

## Next Steps
- Fix Priority: High issues immediately
- Re-test failed tests
- Deploy fixes
- Re-run full suite
```

---

## Success Criteria

Agent is production-ready when:

- ✅ Unit test pass rate >95%
- ✅ Stress test pass rate >90%
- ✅ 20x variance <20%
- ✅ Zero critical failures (compliance, voice violations in own output)
- ✅ Knowledge retrieval >90% success rate
- ✅ User acceptance testing: 3/3 writers approve

---

## Regression Testing

After ANY change to:
- System instructions
- Topic instructions
- SharePoint documents
- Copilot Studio settings

Run:
1. Critical unit tests (20 tests covering all topics)
2. Voice compliance tests (10 tests)
3. Knowledge retrieval tests (5 tests)

**Before deploying changes to production.**

---

This testing framework ensures the SurePayroll Content Agent performs correctly, consistently, and reliably under all conditions.
