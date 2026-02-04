# Walkthrough: Retro Facilitator

Build a skill that guides retrospectives and produces actionable summaries.

**Time:** 45-60 minutes

---

## Step 1: Understand the Problem (5 min)

Retrospectives often fail because:
- No structure → rambling discussions
- No facilitation → loudest voices dominate
- No action items → nothing changes
- No documentation → learnings lost

A good retro facilitator:
- Guides through phases
- Keeps things moving
- Synthesizes themes
- Produces clear action items

This is a **multi-step interactive skill** — more complex than previous exercises.

---

## Step 2: Create the File (2 min)

```markdown
# Retro Facilitator

Guide sprint retrospectives and produce actionable summaries.
```

---

## Step 3: Define Triggers (2 min)

```markdown
## Triggers

Use this skill when the user:
- Asks to "run a retro" or "facilitate retro"
- Wants help with "sprint retrospective"
- Says "let's do a retro"
- Asks to "wrap up the sprint"
```

---

## Step 4: Design the Flow (10 min)

Unlike previous skills, this one has **phases**:

```markdown
## Workflow Phases

### Phase 1: Setup
- Get sprint/period context
- Confirm format (standard, 4Ls, Start/Stop/Continue)
- Set expectations

### Phase 2: What Went Well (5 min)
- Collect positives
- Acknowledge wins
- Note patterns

### Phase 3: What Could Improve (5 min)
- Collect pain points
- No solutions yet — just identify
- Create safe space for honesty

### Phase 4: Themes (2 min)
- Group similar items
- Identify root causes
- Highlight patterns across feedback

### Phase 5: Actions (5 min)
- Brainstorm solutions
- Prioritize by impact/effort
- Assign owners + deadlines

### Phase 6: Summary
- Document everything
- Create shareable output
- Note follow-up items
```

---

## Step 5: Write Instructions (10 min)

```markdown
## Instructions

1. **Start the retro:**
   - Ask: "What sprint/period are we reflecting on?"
   - Ask: "Any specific context I should know?"
   - Confirm format (default to Good/Bad/Actions)

2. **Collect "What Went Well":**
   - Prompt: "What went well this sprint? Share wins, good practices, things to keep doing."
   - Acknowledge each item positively
   - When input slows, summarize and move on

3. **Collect "What Could Improve":**
   - Prompt: "What was challenging or frustrating? What could be better?"
   - Remain neutral — no defending or fixing yet
   - Encourage specifics over vague complaints

4. **Identify Themes:**
   - Look for patterns across both lists
   - Group related items
   - Call out: "I'm seeing a theme around X..."
   - Ask: "Does this resonate?"

5. **Generate Actions:**
   - For each major theme, ask: "What's one concrete thing we could do?"
   - Push for specificity: WHO will do WHAT by WHEN
   - Limit to 2-4 actions (more won't get done)

6. **Produce Summary:**
   - Format in standard template
   - Make it shareable (Slack, wiki, etc.)
   - Include follow-up mechanism
```

---

## Step 6: Define Output Format (3 min)

```markdown
## Output Format

\`\`\`markdown
# Sprint Retro: [Sprint Name]
**Date:** YYYY-MM-DD
**Participants:** [if provided]
**Facilitator:** Claude

---

## 🌟 What Went Well
- Item 1
- Item 2
- Item 3

## 🔧 What Could Improve
- Item 1
- Item 2
- Item 3

## 🎯 Themes Identified

**Theme 1: [Name]**
Related items: [list]
Root cause: [if identified]

**Theme 2: [Name]**
Related items: [list]

## ✅ Action Items

| Action | Owner | Due | Success Metric |
|--------|-------|-----|----------------|
| Specific action 1 | @person | Date | How we'll know it worked |
| Specific action 2 | @person | Date | Metric |

## 📝 Parking Lot
[Items raised but not addressed this retro]

## 🔄 Follow-up
- Review actions at next retro
- [Owner] to schedule follow-up if needed
\`\`\`
```

---

## Step 7: Add Examples (10 min)

```markdown
## Examples

### Example: Interactive Flow

**User:** Let's do a retro for Sprint 23

**Claude:** Great! Let's reflect on Sprint 23. 

Quick setup:
- **Format:** I'll use Good/Bad/Actions. Want a different format (4Ls, Start/Stop/Continue)?
- **Context:** Anything specific about this sprint I should know?

**User:** Standard format is fine. We shipped the new dashboard but it was rough.

**Claude:** Got it — dashboard shipped but bumpy. Let's dig in.

**🌟 What Went Well**
What were the wins this sprint? What should we keep doing?

**User:** 
- Dashboard shipped on time
- New monitoring caught a bug before users did
- Good collaboration between frontend and backend

**Claude:** Nice wins! Shipping on time + catching bugs proactively. 

**🔧 What Could Improve**
What was frustrating? What slowed you down?

**User:**
- Requirements kept changing mid-sprint
- Too many meetings
- Deployments were scary — no rollback plan

**Claude:** I hear you on the changing requirements and meeting overload. The deployment concern is important too.

**🎯 Themes I'm Seeing:**

1. **Scope Stability** — Requirements changing mid-sprint suggests planning or stakeholder alignment issues

2. **Meeting Load** — Too many meetings eating into focus time

3. **Deployment Confidence** — Fear around releases indicates need for better safety nets

Do these resonate?

**User:** Yes, especially 1 and 3. Meetings are annoying but less critical.

**Claude:** Let's focus actions on scope and deployments.

**✅ Actions**

For **Scope Stability:**
- What's one thing that would help? Maybe a change freeze mid-sprint?

**User:** We should require PM sign-off for any mid-sprint changes

**Claude:** Good. Who owns making that happen?

**User:** I'll talk to Sarah (PM) about it this week

**Claude:** 
Action 1: "Ray to align with Sarah on mid-sprint change process by Friday"

For **Deployment Confidence:**
- What would make deploys less scary?

**User:** Automated rollback if error rate spikes

**Claude:** 
Action 2: "Implement automated rollback trigger — who owns this?"

**User:** That's a backend thing, Miguel can own it

**Claude:** Timeline?

**User:** Next sprint

**Claude:** Got it. Here's your retro summary:

[Outputs full formatted summary]

---

### Example: Summary Output

# Sprint Retro: Sprint 23
**Date:** 2024-01-15
**Facilitator:** Claude

---

## 🌟 What Went Well
- Dashboard shipped on time despite challenges
- New monitoring system caught bug before user impact
- Strong frontend/backend collaboration

## 🔧 What Could Improve
- Requirements changed mid-sprint causing rework
- Too many meetings reduced focus time
- Deployments felt risky without rollback plan

## 🎯 Themes Identified

**Theme 1: Scope Stability**
Mid-sprint requirement changes disrupted flow and caused rework.

**Theme 2: Deployment Confidence**
Team hesitant to deploy due to lack of safety nets.

## ✅ Action Items

| Action | Owner | Due | Success Metric |
|--------|-------|-----|----------------|
| Align with PM on mid-sprint change process | Ray | Fri 1/19 | Documented process |
| Implement automated rollback on error spike | Miguel | Sprint 24 | Rollback triggers in staging |

## 📝 Parking Lot
- Meeting overload — revisit if it persists

## 🔄 Follow-up
- Review these actions at Sprint 24 retro
```

---

## Step 8: Handle Edge Cases (3 min)

```markdown
## Notes

- If user dumps everything at once, still structure it into phases
- If no pain points mentioned, probe gently: "What would you do differently?"
- If too many action items, help prioritize: "Which 2 would have most impact?"
- For solo retros, adjust language (no "team" references)
- Keep energy positive — retros shouldn't feel like blame sessions
```

---

## Step 9: Test It (5 min)

Run through a real or simulated retro:
1. Start with setup
2. Go through each phase
3. Check that the summary captures everything
4. Verify actions are SMART (Specific, Measurable, Assignable, Realistic, Time-bound)

---

## 🎉 Done!

This is the most complex skill in the workshop. It demonstrates:
- Multi-phase interactive workflows
- Contextual responses based on user input
- Synthesizing and categorizing input
- Producing structured, actionable output

If you can build this, you can build almost any skill!
