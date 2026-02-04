# Exercise 6: Retro Facilitator

**Difficulty:** Advanced  
**Time:** 45-60 minutes

## Goal

Build a skill that guides sprint retrospectives and produces actionable summaries.

## What You'll Learn

- Multi-step workflows
- Conversational interaction
- Synthesizing group input
- Action item extraction

## Requirements

Your skill should:
1. Guide through retro phases (Good/Bad/Actions)
2. Prompt for input at each phase
3. Identify themes across feedback
4. Generate prioritized action items
5. Produce a shareable summary

## Getting Started

1. Create `SKILL.md` in this folder
2. Think about the facilitator's role
3. Balance structure with flexibility

## Retro Flow

```
1. SET CONTEXT
   - Sprint/period being reviewed
   - Team context if relevant

2. WHAT WENT WELL (5 min)
   - Collect positives
   - Acknowledge wins

3. WHAT COULD IMPROVE (5 min)  
   - Collect pain points
   - No solutions yet

4. IDENTIFY THEMES (2 min)
   - Group similar items
   - Highlight patterns

5. ACTION ITEMS (5 min)
   - Concrete next steps
   - Assign owners
   - Set deadlines

6. SUMMARY
   - Document for the team
```

## Output Format

```markdown
# Sprint Retro: [Sprint Name]
**Date:** YYYY-MM-DD  
**Participants:** [if provided]

## 🌟 What Went Well
- Item 1
- Item 2

## 🔧 What Could Improve  
- Item 1
- Item 2

## 🎯 Themes Identified
1. **Theme:** [description]
2. **Theme:** [description]

## ✅ Action Items
| Action | Owner | Due |
|--------|-------|-----|
| Do X | @person | Date |

## 📝 Notes
[Any additional context]
```

## Hints

<details>
<summary>Hint 1: Facilitate, don't dominate</summary>

Good facilitators:
- Ask open-ended questions
- Summarize without editorializing  
- Keep things moving
- Make sure everyone's heard

</details>

<details>
<summary>Hint 2: Theme detection</summary>

Look for:
- Repeated words/concepts
- Related pain points
- Connected root causes

Group items that share underlying issues.

</details>

## Stretch Goals

- Track retro history across sprints
- Measure action item completion rate
- Suggest retro formats (Start/Stop/Continue, 4Ls, etc.)
- Generate team health metrics
