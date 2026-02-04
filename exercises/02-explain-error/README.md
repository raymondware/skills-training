# Exercise 2: Error Explainer

**Difficulty:** Beginner  
**Time:** 15-20 minutes

## Goal

Build a skill that takes error messages/stack traces and explains them in plain English with fix suggestions.

## What You'll Learn

- Text parsing and analysis
- Providing actionable guidance
- Handling varied input formats

## Requirements

Your skill should:
1. Accept an error message or stack trace
2. Identify the error type and root cause
3. Explain what went wrong in plain English
4. Suggest 1-3 ways to fix it

## Getting Started

1. Create `SKILL.md` in this folder
2. Think about different error formats (JS, Python, etc.)
3. Focus on being helpful, not just accurate

## Test Cases

```javascript
// JavaScript
TypeError: Cannot read property 'map' of undefined

// Python
KeyError: 'username'

// General
ECONNREFUSED 127.0.0.1:5432
```

## Hints

<details>
<summary>Hint 1: Structure your explanation</summary>

1. What happened (one sentence)
2. Why it happened (context)
3. How to fix it (actionable steps)

</details>

<details>
<summary>Hint 2: Common patterns</summary>

- `undefined`/`null` → something wasn't initialized
- `ECONNREFUSED` → service not running
- `KeyError`/`TypeError` → wrong data shape

</details>

## Stretch Goals

- Detect the programming language automatically
- Link to relevant documentation
- Suggest debugging steps
