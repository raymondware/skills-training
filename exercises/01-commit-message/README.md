# Exercise 1: Commit Message Generator

**Difficulty:** Beginner  
**Time:** 15-20 minutes

## Goal

Build a skill that generates conventional commit messages from staged git changes.

## What You'll Learn

- Basic skill structure
- Using shell commands (`git diff`)
- Structured output formatting
- Handling different scenarios

## Requirements

Your skill should:
1. Read staged changes with `git diff --staged`
2. Identify the type of change (feat/fix/docs/etc)
3. Generate a properly formatted conventional commit
4. Handle both simple and complex changesets

## Getting Started

1. Create a file called `SKILL.md` in this folder
2. Use the template from `templates/SKILL-TEMPLATE.md`
3. Fill in each section

## Test Cases

Try your skill with these scenarios:

| Scenario | Expected Type |
|----------|---------------|
| New React component added | `feat` |
| Fixed null pointer bug | `fix` |
| Updated README | `docs` |
| Renamed variables for clarity | `refactor` |
| Added unit tests | `test` |

## Hints

<details>
<summary>Hint 1: Reading staged changes</summary>

Use `git diff --staged` to see what's about to be committed.
For a summary, try `git diff --staged --stat`.

</details>

<details>
<summary>Hint 2: Conventional commit format</summary>

```
type(scope): description

[optional body]

[optional footer]
```

</details>

<details>
<summary>Hint 3: Keep it simple first</summary>

Start with just type + description. Add scope and body handling after the basics work.

</details>

## Solution

See `examples/commit-message/SKILL.md` for a reference implementation.

## Stretch Goals

- Add support for breaking changes (BREAKING CHANGE footer)
- Detect if changes should be split into multiple commits
- Support for issue/ticket references
