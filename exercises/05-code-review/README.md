# Exercise 5: Code Review

**Difficulty:** Intermediate  
**Time:** 30-40 minutes

## Goal

Build a skill that performs structured code reviews with actionable feedback.

## What You'll Learn

- File analysis patterns
- Structured feedback format
- Balancing critique with praise
- Prioritizing issues

## Requirements

Your skill should:
1. Accept a file path or diff
2. Review for: bugs, security, performance, readability
3. Categorize findings by severity
4. Include specific line references
5. Suggest fixes, not just problems

## Getting Started

1. Create `SKILL.md` in this folder
2. Define clear review categories
3. Think about what makes feedback actionable

## Output Format Suggestion

```markdown
## Code Review: [filename]

### Summary
[1-2 sentence overview]

### 🔴 Critical
- **Line X:** [Issue] → [Suggested fix]

### 🟡 Suggestions  
- **Line X:** [Issue] → [Suggested fix]

### 🟢 Good Practices
- [What's done well]

### Overall
[Approval status + next steps]
```

## Review Checklist

**Bugs**
- Null/undefined handling
- Edge cases
- Error handling

**Security**
- Input validation
- SQL injection
- XSS vulnerabilities
- Secrets in code

**Performance**
- N+1 queries
- Unnecessary re-renders
- Memory leaks

**Readability**
- Naming conventions
- Function length
- Comments where needed

## Hints

<details>
<summary>Hint: Prioritize ruthlessly</summary>

Don't dump 50 nitpicks. Focus on:
1. Bugs that will break prod
2. Security issues
3. Major readability problems

Leave minor style issues for linters.

</details>

## Stretch Goals

- Integrate with `git diff` for PR reviews
- Auto-suggest which files need most attention
- Generate approval/request-changes summary
