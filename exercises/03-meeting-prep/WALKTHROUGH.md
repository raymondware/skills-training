# Walkthrough: Meeting Prep

Build a skill that turns a meeting topic into a structured agenda.

**Time:** 15-20 minutes

---

## Step 1: Create the File (1 min)

```markdown
# Meeting Prep

Generate meeting agendas, talking points, and questions from a topic.
```

---

## Step 2: Define Triggers (2 min)

```markdown
## Triggers

Use this skill when the user:
- Asks to "prep for a meeting"
- Wants help with a "meeting agenda"
- Says "I have a meeting about X"
- Asks for "talking points" for a discussion
```

---

## Step 3: Write Instructions (5 min)

Think about what makes meetings effective:

```markdown
## Instructions

1. Understand the meeting context:
   - What type? (1:1, planning, demo, interview, etc.)
   - Who's attending? (if mentioned)
   - What's the goal?

2. Generate appropriate structure based on type:
   - 1:1 → relationship, updates, blockers, growth
   - Planning → scope, risks, assignments, timeline
   - Demo → setup, walkthrough, Q&A
   - Interview → introductions, questions, candidate questions

3. Create agenda with time estimates
4. List key talking points
5. Generate relevant questions to ask
6. Note any prep work needed
```

---

## Step 4: Define Output Format (3 min)

```markdown
## Output Format

\`\`\`markdown
## Meeting: [Topic]
**Type:** [meeting type]
**Duration:** [suggested time]

### Agenda
1. [Item] (X min)
2. [Item] (X min)
3. [Item] (X min)

### Key Points to Cover
- Point 1
- Point 2
- Point 3

### Questions to Ask
- Question 1?
- Question 2?
- Question 3?

### Prep Checklist
- [ ] Prep item 1
- [ ] Prep item 2
\`\`\`
```

---

## Step 5: Add Examples (5 min)

Different meeting types need different approaches:

```markdown
## Examples

### Example 1: 1:1 with manager

**Input:** "I have a 1:1 with my manager tomorrow, want to discuss promotion"

**Output:**

## Meeting: Career Discussion 1:1
**Type:** 1:1
**Duration:** 30 min

### Agenda
1. Quick wins / recent accomplishments (5 min)
2. Promotion discussion (15 min)
3. Next steps and timeline (5 min)
4. Any blockers or support needed (5 min)

### Key Points to Cover
- Specific achievements since last review
- Examples of operating at next level
- Your understanding of promotion criteria
- Timeline expectations

### Questions to Ask
- What does success look like for promotion this cycle?
- What gaps, if any, do you see in my readiness?
- Who else should I be talking to?
- What projects would help demonstrate readiness?

### Prep Checklist
- [ ] List 3-5 concrete accomplishments with impact
- [ ] Review promotion criteria/rubric
- [ ] Prepare examples of next-level work
- [ ] Think about your ideal timeline

---

### Example 2: Sprint planning

**Input:** "sprint planning for the new auth feature"

**Output:**

## Meeting: Auth Feature Sprint Planning
**Type:** Planning
**Duration:** 60 min

### Agenda
1. Review requirements and acceptance criteria (10 min)
2. Break down into tasks (20 min)
3. Estimate and assign (15 min)
4. Identify risks and dependencies (10 min)
5. Commit to sprint goal (5 min)

### Key Points to Cover
- OAuth vs username/password scope
- Security requirements (2FA, rate limiting)
- Integration points with existing system
- Testing strategy

### Questions to Ask
- What's the MVP vs nice-to-have?
- Any compliance requirements?
- Do we need security review before merge?
- What's the rollout plan (feature flag)?

### Prep Checklist
- [ ] Review PRD/requirements doc
- [ ] Check existing auth code
- [ ] List technical unknowns
- [ ] Identify who needs to be involved
```

---

## Step 6: Handle Edge Cases (2 min)

```markdown
## Notes

- If meeting type is unclear, ask or make reasonable assumption
- Default to 30 min if duration not specified
- Adjust formality based on context (exec meeting vs team sync)
- For recurring meetings, focus on what's new/different
```

---

## Step 7: Test It (3 min)

Try these prompts:
1. "Prep me for a client demo of our dashboard tomorrow"
2. "I have a skip-level with my director"  
3. "Interviewing a senior engineer at 2pm"

Check:
- Is the agenda realistic for the time?
- Are questions actually useful?
- Is the prep checklist actionable?

---

## 🎉 Done!

You've built a skill that makes meetings more productive before they even start. The key insight: different meeting types have different structures.
