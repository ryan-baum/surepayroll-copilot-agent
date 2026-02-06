# SurePayroll Content Agent - Quick Reference Card

## 🎯 One-Page Implementation Cheat Sheet

---

## Deployment Checklist (3-4 Hours)

### ☐ Phase 1: SharePoint (60-90 min)
- [ ] Create site: "SurePayroll Content System"
- [ ] Create 3 folders: Core_Documentation, Implementation_Research, Examples
- [ ] Upload 11 docs to Core_Documentation
- [ ] Add headers to all docs (copy template from 01_SharePoint_Structure.md)
- [ ] Create 3 example files in Examples folder
- [ ] Configure metadata columns (optional but recommended)

### ☐ Phase 2: Agent Setup (90-120 min)
- [ ] Create agent: "SurePayroll Content Production Assistant"
- [ ] Paste system instructions from 02_Agent_System_Instructions.md
- [ ] Add SharePoint knowledge source (point to site URL)
- [ ] Enable: Generative orchestration + Semantic search
- [ ] Wait for indexing (5-10 min) → Status: Ready

### ☐ Phase 3: Topics (60-90 min)
- [ ] Create Topic 1: Brief Generation (copy from 03_Agent_Topics)
- [ ] Create Topic 2: Outline Creation
- [ ] Create Topic 3: First Draft Writing
- [ ] Create Topic 4: Editorial Review
- [ ] Create Topic 5: Writer Revision Support
- [ ] Create Topic 6: Final Polish & Compliance
- [ ] Create Topic 7: Quality Gate Decision

### ☐ Phase 4: Testing (30-45 min)
- [ ] Test: "What are the 7 Content Code principles?" → Should retrieve Content_Code.md
- [ ] Test: "Create brief for payroll deadlines" → Should trigger Topic 1
- [ ] Test: "Review this: 'We're excited!'" → Should flag voice violation
- [ ] Run full workflow: Brief → Outline → Draft → Review → Revision → Polish → Gate
- [ ] Check pass criteria: Topics route correctly, docs retrieved, voice enforced

### ☐ Phase 5: Launch (15-30 min)
- [ ] Create Writer Quick Start guide
- [ ] Train first writer (30 min)
- [ ] Monitor first 3 pieces closely
- [ ] Iterate based on feedback

---

## Quick Command Reference

### Writer Queries

| Stage | Say This | Agent Does |
|-------|----------|------------|
| Brief | "Create brief for [topic]" | Generates brief with IG verification |
| Outline | "Create outline from brief" | Builds H2/H3 structure with BLUF |
| Draft | "Write first draft" | Full draft in SurePayroll voice |
| Review | "Review this draft" | Scores 1-10, checks CC1-CC7 |
| Revision | "Help me revise" | Guides through priority fixes |
| Polish | "Final compliance check" | Line edit + compliance |
| Gate | "Ready to publish?" | Binary PASS/FAIL decision |

### Help Queries

- "What are voice rules?"
- "Show example of strong brief"
- "What is CC1?"
- "How do I fix this section?"
- "Why does this feel off?"

---

## Critical Settings

### System Instructions Location
**Copilot Studio** → Your Agent → Settings → Generative AI → Instructions

### Key Settings to Enable
- ✅ **Generative orchestration:** Settings → Generative AI → Advanced
- ✅ **Semantic search:** Knowledge → Settings → Tenant graph grounding

### SharePoint Knowledge Source
- **Path:** [Your Site]/SurePayroll Content System
- **Include subfolders:** Yes
- **Refresh:** Weekly
- **File limit:** 36,000 characters per file

---

## Voice Rules (Quick Check)

### ❌ NEVER Use:
- Exclamation points
- "We're excited/thrilled/delighted"
- "You might want to consider"
- "It's important to note"
- "Feel free to"
- "Don't worry"

### ✅ ALWAYS Use:
- Confident and direct language
- BLUF structure (answer first)
- Specific evidence for claims
- Calm, practical tone

---

## Quality Standards

### Minimum for Publication
- **Quality Score:** 6+ on 10-point scale
- **Content Code:** All 7 principles pass
- **Information Gain:** 3 specific unique contributions
- **Compliance:** No guarantee language, disclaimers present
- **Voice:** Zero violations

### Quality Gate Pass Criteria
- ✅ All CC1-CC7 principles satisfied
- ✅ Voice sounds like SurePayroll
- ✅ Score 6+ estimated
- ✅ Delivers brief requirements
- ✅ Compliance cleared
- ✅ Product integration natural

---

## 7 Content Code Principles (CC1-CC7)

| # | Principle | Quick Check |
|---|-----------|-------------|
| CC1 | Move readers forward | Natural product integration? |
| CC2 | Justify existence (3 dimensions) | Unique value for reader/business/landscape? |
| CC3 | Think like Owners | Distribution plan clear? |
| CC4 | Clarity > Brevity > Cleverness | No throat-clearing? |
| CC5 | Clear POV with authority | Takes stance with evidence? |
| CC6 | Layered credibility | Paychex data first? |
| CC7 | Answer questions + one more | Anticipates next question? |

---

## Information Gain Verification

### Required for Every Brief

**3 Unique Contributions:**
1. What does this add that Google's top 5 don't have?
2. What proprietary data/expert quote/unique angle?
3. What contrarian or differentiated perspective?

**Kill Switch Triggers If:**
- Can't articulate 3 specific contributions
- No originality signal (data, expert, unique angle)
- Topic too generic ("payroll tips")

---

## Testing Quick Checks

### Unit Tests (Must Pass)
- [ ] Each topic triggers with trigger phrase
- [ ] SharePoint docs retrieved (test with CC1-CC7 query)
- [ ] Voice violations detected (test with "we're excited!")
- [ ] Full workflow completes (Brief → Gate)

### Stress Tests (Before Launch)
- [ ] 10 concurrent conversations (no errors)
- [ ] 100+ turn conversation (context retained)
- [ ] 20x same query (variance <20%)

---

## Troubleshooting Quick Fixes

| Problem | Quick Fix |
|---------|-----------|
| Topics not triggering | Check generative orchestration enabled |
| Docs not retrieved | Verify indexing complete (Knowledge → Status) |
| Voice not enforced | Check Voice_Tone.md is indexed |
| Agent too lenient | Review Quality_Standards.md clarity |

---

## File Sizes (SharePoint Limit)

**Maximum:** 36,000 characters per file

**Check Your Docs:**
1. Open in text editor
2. Select all (Ctrl+A)
3. Paste into character counter
4. If >36k, split into Part1/Part2

---

## Success Metrics

### Track Weekly
- Conversations per week
- Topics triggered (which stages used)
- Quality scores at Final Polish

### Track Monthly
- % passing Quality Gate first time (target: 80%+)
- Average time Brief → Published (target: <5 days)
- Voice violations per piece (target: <3)

---

## Emergency Contacts

**Technical Issues:**
- IT/M365 Admin: _____________
- Copilot Studio Support: Microsoft Learn docs

**Content Issues:**
- Content Lead: _____________
- Review documentation in SharePoint

**System Improvements:**
- Document in Implementation_Research folder
- Review at quarterly check-in

---

## Version Control

**Current Version:** 1.0 (2026-02-05)

**When to Update:**
- Content Code principles change
- Voice guidelines revised
- New workflow stage added
- Major pattern identified

**How to Update:**
1. Edit system instructions or topic
2. Test with critical unit tests
3. Deploy to production
4. Monitor for regressions

---

## Daily Operations

### Writer Workflow
1. Start conversation: "Create brief for [topic]"
2. Review brief → if approved: "Create outline"
3. Review outline → if approved: "Write first draft"
4. Submit draft: "Review this draft"
5. Apply feedback: "Help me revise"
6. Final check: "Final compliance check"
7. Gate decision: "Ready to publish?"

### Editor Review Points
- Brief: IG verified? Quality cliff assessed?
- Outline: BLUF applied? Product integration natural?
- Draft: Voice clean? Evidence present?
- Final: Compliance clear? Ready to publish?

---

## Key Files Quick Access

| Need | File | Location |
|------|------|----------|
| Setup instructions | 04_Deployment_Guide.md | Phase-by-phase guide |
| System instructions | 02_Agent_System_Instructions.md | Copy/paste into agent |
| Topic configurations | 03_Agent_Topics_Configuration.md | Copy each topic |
| Testing checklist | 05_Testing_Framework.md | Pre/post launch tests |
| Quality assessment | 06_Implementation_Evaluation_Rubric.md | Evaluate implementation |

---

## Pre-Launch Checklist

### Before Going Live:
- [ ] All 7 topics created and tested
- [ ] SharePoint indexed (14 files: 11 docs + 3 examples)
- [ ] Unit tests pass (>95%)
- [ ] Full workflow tested (Brief → Gate)
- [ ] Voice compliance verified
- [ ] 2-3 writers trained
- [ ] Quick Start guide created
- [ ] Monitoring plan in place

### Week 1 After Launch:
- [ ] Daily analytics review
- [ ] Fix any routing issues
- [ ] Collect writer feedback
- [ ] Document common questions
- [ ] Refine topic descriptions if needed

---

## Quick Wins (If Struggling)

**Can't deploy entire system?**
→ Start with Topic 1 (Brief) + Topic 4 (Review)
→ Most value with minimal setup

**Writers resistant?**
→ Position as "content coach" not "AI replacement"
→ Show examples of improved quality

**Quality inconsistent?**
→ Run 20x test to measure variance
→ Add more examples to SharePoint
→ Tighten topic instructions

---

**📞 Need Help?**

1. Check `04_Deployment_Guide.md` → Troubleshooting section
2. Review `README.md` for overview
3. Use `06_Implementation_Evaluation_Rubric.md` to diagnose gaps

---

**✅ You're Ready!**

Print this card, follow the checklist, and deploy your agent in 3-4 hours.

Start with Phase 1 (SharePoint setup) and work through sequentially.
