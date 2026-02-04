# Exercise 3: Meeting Prep

**Difficulty:** Beginner  
**Time:** 15-20 minutes

## Goal

Build a skill that generates meeting agendas, talking points, and questions from a topic or context.

## What You'll Learn

- Working with unstructured input
- Generating structured output
- Adding value beyond simple formatting

## Requirements

Your skill should:
1. Accept a meeting topic or context
2. Generate a structured agenda
3. Include talking points and time estimates
4. Suggest questions to ask

## Getting Started

1. Create `SKILL.md` in this folder
2. Think about what makes meetings effective
3. Output should be copy-paste ready

## Test Cases

| Input | Expected Output |
|-------|-----------------|
| "1:1 with manager about promotion" | Career-focused agenda |
| "Sprint planning for auth feature" | Technical planning agenda |
| "Client demo of new dashboard" | Demo-focused agenda |

## Output Format Suggestion

```markdown
## Meeting: [Topic]
**Duration:** X minutes

### Agenda
1. [Item] (X min)
2. [Item] (X min)

### Key Points to Cover
- Point 1
- Point 2

### Questions to Ask
- Question 1?
- Question 2?

### Prep Needed
- [ ] Task 1
- [ ] Task 2
```

## Hints

<details>
<summary>Hint: Think about meeting types</summary>

Different meetings need different structures:
- 1:1s → relationship + career + blockers
- Planning → scope + risks + assignments
- Demos → setup + walkthrough + Q&A

</details>

## Stretch Goals

- Detect meeting type automatically
- Integrate with calendar context
- Generate follow-up email template
