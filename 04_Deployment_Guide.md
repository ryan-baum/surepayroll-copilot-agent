# SurePayroll Content Agent - Complete Deployment Guide

## Overview

This guide provides step-by-step instructions to deploy the SurePayroll Content Production Agent in Microsoft Copilot Studio.

**Estimated Setup Time:** 3-4 hours
**Prerequisites:** Microsoft 365 Copilot Studio access, SharePoint site admin rights

---

## Phase 1: SharePoint Setup (60-90 minutes)

### Step 1.1: Create SharePoint Site

1. Navigate to SharePoint admin center
2. Click **Create** → **Site**
3. Select **Team site**
4. Configure:
   - **Site name:** SurePayroll Content System
   - **Description:** Reference documentation and examples for AI-assisted content production
   - **Privacy:** Private (only content team members)
5. Click **Finish**

### Step 1.2: Create Folder Structure

In the new site, create this structure:

```
Documents/
├── Core_Documentation/
├── Implementation_Research/
└── Examples/
```

**How to create folders:**
1. Go to **Documents** library
2. Click **+ New** → **Folder**
3. Name folder exactly as shown above
4. Repeat for all three folders

### Step 1.3: Upload Existing Documents

Upload these 11 files to **Core_Documentation/** folder:
- CONTEXT.md
- Content_Code.md
- Voice_Tone.md
- Grammar_Mechanics.md
- Inclusion_Accessibility.md
- Positioning.md
- Features_Benefits.md
- Quality_Standards.md
- Workflow_Stages.md
- ICP_Personas.md (if available)
- Content_Brief_Template.md (if available)

**Upload process:**
1. Open **Core_Documentation** folder
2. Click **Upload** → **Files**
3. Select all documentation files
4. Wait for upload to complete

### Step 1.4: Add Document Headers (CRITICAL for RAG)

Each document needs a header for better retrieval. Edit each file:

1. Open document in SharePoint
2. Add this header at the TOP:

```markdown
---
Document: [Document Name]
Category: Core Documentation
Topics: [relevant, keywords, here]
Last Updated: 2026-02-05
---

## Summary
[2-3 sentence overview]

## When to Use This Document
[Clear triggering conditions]

---

[Original content...]
```

**Example for Content_Code.md:**

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
- Making editorial decisions
- Resolving content direction conflicts

---

# SurePayroll Content Code

[Rest of original content...]
```

Repeat for all 11 documents.

### Step 1.5: Create Example Files (NEW - Required)

Research shows 2-3 examples dramatically improve quality. Create these files in **Examples/** folder:

**Create: Example_Brief_Strong.md**
- Copy content from `01_SharePoint_Structure.md` → Example_Brief_Strong section
- Save in Examples/ folder

**Create: Example_Brief_Weak.md**
- Copy content from `01_SharePoint_Structure.md` → Example_Brief_Weak section
- Save in Examples/ folder

**Create: Example_Outline_Strong.md**
- Copy content from `01_SharePoint_Structure.md` → Example_Outline_Strong section
- Save in Examples/ folder

You now have 14 total files in SharePoint.

### Step 1.6: Configure Document Metadata (Optional but Recommended)

1. Go to **Library settings**
2. Click **Create column**
3. Add these columns:

| Column Name | Type | Choices |
|-------------|------|---------|
| ContentStage | Choice | Briefing, Outline, First Draft, Editorial Review, Writer Revision, Final Edit, Published |
| DocumentType | Choice | Core Reference, Workflow Guide, Example Content, Research |
| CharacterCount | Number | (leave blank - will track manually) |
| LastVerified | Date | Today's date |

4. Click **OK** to create each column

### Step 1.7: Verify File Sizes

SharePoint RAG has 36,000 character limit per file. Check:

1. Open each document
2. Select all text (Ctrl+A / Cmd+A)
3. Paste into character counter (e.g., wordcounter.net)
4. If any file exceeds 36,000 characters, split into two files:
   - Original_Document_Part1.md
   - Original_Document_Part2.md

**Phase 1 Complete** ✅
You now have a RAG-optimized SharePoint knowledge base.

---

## Phase 2: Copilot Studio Agent Creation (90-120 minutes)

### Step 2.1: Create New Agent

1. Navigate to [Copilot Studio](https://copilotstudio.microsoft.com)
2. Click **Create** → **New agent**
3. Configure:
   - **Name:** SurePayroll Content Production Assistant
   - **Description:** AI assistant for creating high-quality marketing content following SurePayroll standards
   - **Language:** English
4. Click **Create**

### Step 2.2: Configure System Instructions

1. In your new agent, click **Settings** (gear icon)
2. Navigate to **Generative AI** → **Instructions**
3. Copy the ENTIRE contents from `02_Agent_System_Instructions.md` → System Instructions section
4. Paste into the **Instructions** field
5. Click **Save**

### Step 2.3: Configure Generative AI Settings

Still in Settings → Generative AI:

| Setting | Value |
|---------|-------|
| **How should your copilot interact with users?** | "Professional, direct, and actionable. Provide specific feedback with concrete examples." |
| **Content moderation** | Medium |
| **Response length** | Medium to Long |

Click **Save**

### Step 2.4: Add SharePoint Knowledge Source

1. Navigate to **Knowledge** → **+ Add knowledge**
2. Select **SharePoint**
3. Configure:
   - **SharePoint site:** Paste URL of "SurePayroll Content System" site
   - **Include subfolders:** Yes
   - **Refresh frequency:** Weekly
4. Click **Add**
5. Wait for indexing (5-10 minutes)

**Verify indexing:**
1. Go to **Knowledge** tab
2. You should see ~14 files listed
3. Status should show "Ready"

### Step 2.5: Enable Advanced Settings (CRITICAL)

1. Settings → **Generative AI** → **Advanced settings**
2. Enable:
   - ✅ **Generative orchestration** (allows conversational routing)
   - ✅ **Tenant graph grounding with semantic search** (improves SharePoint retrieval)
3. Click **Save**

**Phase 2.1 Complete** ✅
Agent created with system instructions and knowledge source connected.

---

## Phase 3: Create 7 Workflow Topics (60-90 minutes)

### Topic Creation Process (repeat 7 times)

For each topic in `03_Agent_Topics_Configuration.md`:

1. Navigate to **Topics** → **+ Add topic** → **From blank**
2. Fill in:
   - **Name:** [From topic spec]
   - **Description:** [CRITICAL - copy exactly from spec for AI routing]
3. Click **Create**

4. **Add Trigger Phrases:**
   - Click **Trigger phrases**
   - Add each phrase from spec (5-10 phrases per topic)
   - Click **Save**

5. **Add Topic Instructions:**
   - Click on the topic canvas
   - Add node: **Message**
   - In message settings, click **Edit with Copilot**
   - Paste the full **Topic Instructions** from the spec
   - Format as markdown
   - Click **Save**

6. **Test Topic:**
   - Click **Test** button
   - Type one of the trigger phrases
   - Verify topic activates correctly
   - Check that it retrieves SharePoint docs

7. Repeat for all 7 topics:
   - Topic 1: Brief Generation
   - Topic 2: Outline Creation
   - Topic 3: First Draft Writing
   - Topic 4: Editorial Review
   - Topic 5: Writer Revision Support
   - Topic 6: Final Polish & Compliance
   - Topic 7: Quality Gate Decision

### Topic Ordering (Optional)

Arrange topics in workflow order for easier management:
1. Go to Topics list
2. Drag to reorder 1-7

**Phase 3 Complete** ✅
All 7 workflow topics created and configured.

---

## Phase 4: Testing & Validation (30-45 minutes)

### Test 1: System Instruction Test

**Query:** "What are the 7 Content Code principles?"
**Expected:** Agent retrieves Content_Code.md and summarizes CC1-CC7

**If it fails:**
- Check Knowledge source is indexed
- Verify Content_Code.md is in SharePoint
- Check system instructions are saved

### Test 2: Topic Routing Test

Test each topic with trigger phrase:

| Topic | Test Query | Pass Criteria |
|-------|------------|---------------|
| Brief | "Create a brief for an article about payroll deadlines" | Topic 1 activates, retrieves docs, generates brief with IG section |
| Outline | "Create outline from this brief: [paste brief]" | Topic 2 activates, generates BLUF-structured outline |
| Draft | "Write first draft from this outline" | Topic 3 activates, applies voice rules, no exclamation points |
| Review | "Review this draft: [paste draft]" | Topic 4 activates, checks CC1-CC7, provides score |
| Revision | "Help me revise based on this feedback" | Topic 5 activates, guides through priority fixes |
| Polish | "Final compliance check on this draft" | Topic 6 activates, checks compliance, line edits |
| Gate | "Is this ready to publish?" | Topic 7 activates, makes binary PASS/FAIL decision |

**Document results:**
- ✅ PASS: Topic activates correctly, retrieves docs, provides expected output
- ❌ FAIL: [What went wrong]

### Test 3: Voice Compliance Test

**Query:** "Review this text for voice: 'We're so excited to announce our new feature! You might want to give it a try!'"
**Expected:** Agent flags "we're so excited" and "you might want to" as violations, provides specific rewrites

### Test 4: Information Gain Test

**Query:** "Create a brief for 'payroll tips for small businesses'"
**Expected:** Agent should flag this as too generic and trigger kill switch if information gain can't be articulated

### Test 5: Full Workflow Test

Run through complete workflow:
1. "Create a brief for [specific topic]"
2. Review brief output
3. "Create outline from this brief"
4. Review outline output
5. "Write first draft from outline"
6. Review draft output
7. "Review this draft"
8. Review editorial feedback
9. "Help me revise"
10. "Final compliance check"
11. "Is this ready to publish?"

**Success criteria:**
- Agent maintains context through conversation
- Each stage builds on previous
- Voice remains consistent
- Quality standards applied throughout

### Test 6: Retrieval Fallback Test

**Query:** "What does [NonexistentDocument].md say?"
**Expected:** "Unable to retrieve [NonexistentDocument].md. Proceeding with general guidelines. Flag for human review."

**Phase 4 Complete** ✅
Agent tested and validated across all workflows.

---

## Phase 5: User Onboarding (15-30 minutes)

### Create Quick Start Guide for Writers

Create this document in SharePoint → **Core_Documentation/** → **Writer_Quick_Start.md**

```markdown
# SurePayroll Content Agent - Writer Quick Start

## How to Use the Agent

### Starting a New Piece

1. Say: "Create a brief for [topic]"
2. Review the brief - check that information gain is verified
3. If approved: "Create outline from this brief"
4. Review outline structure
5. If approved: "Write first draft from outline"

### Getting Help

- "What are the voice rules?"
- "Show me an example of a strong brief"
- "How do I handle [specific situation]?"
- "Review this section for voice"

### Workflow Stages

1. **Brief** - Plan before writing
2. **Outline** - Structure content
3. **First Draft** - Write full piece
4. **Editorial Review** - Get scored feedback
5. **Revision** - Apply improvements
6. **Final Polish** - Compliance and line editing
7. **Quality Gate** - Final PASS/FAIL

### Voice Rules (Quick Reference)

❌ Never use:
- Exclamation points
- "We're excited"
- "You might want to"
- "It's important to note"

✅ Always:
- Confident and direct
- BLUF (answer first, explain after)
- Specific evidence for claims

### Getting Unstuck

If you're stuck, ask the agent:
- "Why does this feel off?"
- "What's wrong with this section?"
- "How do I fix this voice issue?"

The agent will reference the documentation and give you specific fixes.
```

### Train Team Members

1. Schedule 30-minute session with each writer
2. Walk through:
   - How to access agent
   - Sample workflow (Brief → Outline → Draft)
   - How to ask questions
   - Where to find examples
3. Provide Writer Quick Start guide

**Phase 5 Complete** ✅
Team onboarded and ready to use agent.

---

## Phase 6: Monitoring & Improvement (Ongoing)

### Week 1: Daily Check-ins

Monitor usage:
1. Check Copilot Studio **Analytics** daily
2. Review:
   - How many conversations?
   - Which topics triggered most?
   - Any errors or failures?
3. Adjust topic descriptions if routing is incorrect

### Month 1: Quality Audit

After 30 days:
1. Review 10 pieces created with agent
2. Score against Quality Standards (6+ threshold)
3. Identify patterns:
   - Common failure modes
   - Stages where writers get stuck
   - Topics that need refinement

### Continuous Improvement

**Update system instructions when:**
- Content Code principles change
- Voice guidelines revised
- New patterns identified

**Update topics when:**
- Writers consistently ask same question
- Topic routing fails
- New workflow stage added

**Update examples when:**
- Better examples created
- Standards evolve
- New patterns emerge

---

## Troubleshooting

### Issue: Topics Not Triggering

**Symptoms:** User types trigger phrase, but generic agent responds instead of topic
**Solutions:**
1. Check topic is **enabled** and **published**
2. Verify trigger phrases are saved
3. Check description is clear and detailed (critical for generative orchestration)
4. Try more explicit trigger: "Use the [Topic Name] topic to..."

### Issue: SharePoint Documents Not Retrieved

**Symptoms:** Agent says "Unable to retrieve [document]"
**Solutions:**
1. Verify knowledge source is indexed (Knowledge tab → Status: Ready)
2. Check file is in SharePoint and not deleted
3. Verify file size under 36,000 characters
4. Re-index: Knowledge → Refresh knowledge source
5. Check document headers are added for better retrieval

### Issue: Voice Violations Not Caught

**Symptoms:** Agent doesn't flag "we're excited" or exclamation points
**Solutions:**
1. Check Voice_Tone.md is in SharePoint and indexed
2. Verify Editorial Review topic instructions include voice check section
3. Explicitly say "Check this for voice violations"
4. Update system instructions to emphasize voice rules

### Issue: Agent Too Lenient / Too Strict

**Symptoms:** Scores everything 8-9 OR fails everything
**Solutions:**
1. Review Quality_Standards.md clarity
2. Check if examples (strong/weak) are present
3. Adjust scoring instructions in Editorial Review topic
4. Calibrate with human reviewers

### Issue: Conversation Loses Context

**Symptoms:** Agent forgets earlier parts of workflow
**Solutions:**
1. Use explicit references: "Continue with the brief we created about [topic]"
2. Check conversation token limits (switch to new conversation if very long)
3. Explicitly state stage: "We're at the Outline stage for [topic]"

---

## Maintenance Schedule

| Task | Frequency | Owner |
|------|-----------|-------|
| Review analytics | Weekly | Content Ops |
| Audit content quality | Monthly | Content Lead |
| Update examples | Quarterly | Content Team |
| Refresh SharePoint index | Automatic (weekly) | System |
| Review and update docs | Quarterly | Content Strategist |
| Test all topics | After any doc update | Content Ops |

---

## Success Metrics

Track these to measure agent effectiveness:

### Process Metrics
- Average time per workflow stage
- Number of pieces per week
- Revision cycles per piece

### Quality Metrics
- Average quality score at Final Polish (target: 7+)
- Percentage passing Quality Gate first time (target: 80%+)
- Voice violations per piece (target: <3)

### Efficiency Metrics
- Brief approval rate (target: 90%+)
- Time from Brief to Published (target: <5 days)
- Writer questions per piece (target: decreasing over time)

---

## Rollback Plan

If agent is causing more problems than it solves:

1. **Disable agent temporarily**
   - Settings → Disable agent
   - Revert to manual workflow

2. **Diagnose issue**
   - Review last 10 conversations
   - Identify what's failing
   - Check if docs are outdated

3. **Fix and re-enable**
   - Update problematic topic/instruction
   - Test thoroughly
   - Re-enable agent

4. **Document lesson learned**
   - Add to troubleshooting section
   - Update training materials

---

## Next Steps

After successful deployment:

1. ✅ All 6 phases complete
2. ✅ Team trained
3. ✅ Monitoring in place

**You're ready to use the SurePayroll Content Production Assistant!**

Start with 1-2 pilot pieces, gather feedback, and iterate on the system.

---

## Support & Questions

**For technical issues:**
- Check Troubleshooting section above
- Review Copilot Studio documentation
- Contact IT/M365 admin

**For content questions:**
- Reference SharePoint documentation
- Ask the agent itself: "How should I handle [situation]?"
- Escalate to Content Lead

**For system improvements:**
- Document in `Implementation_Research/` folder
- Propose changes at quarterly review
- Test before deploying to production

---

**Deployment Complete** 🎉

Your SurePayroll Content Production Assistant is now live and ready to help writers create high-quality content efficiently.
