# Claude Code Skills Training

A hands-on workshop for building custom Claude Code skills.

## What Are Skills?

Skills are reusable instruction sets that teach Claude Code how to handle specific tasks. They live in `SKILL.md` files and get loaded when Claude detects a matching trigger.

**Why skills matter:**
- Encode team knowledge and best practices
- Ensure consistent output across projects
- Save time on repetitive workflows
- Share expertise across your organization

## Workshop Structure

| Time | Activity |
|------|----------|
| 10 min | Intro + skill anatomy |
| 10 min | Walk through example skill |
| 30 min | Team builds skills (groups of 2-3) |
| 10 min | Demo + share learnings |

## Skill Anatomy

Every skill has the same basic structure:

```markdown
# Skill Name

Brief description of what this skill does.

## Triggers
When should Claude use this skill? Keywords, phrases, contexts.

## Instructions
Step-by-step guidance for Claude to follow.

## Output Format
What the final output should look like.

## Examples (optional)
Sample inputs → outputs to guide behavior.
```

## Quick Start

1. Pick a skill from `exercises/` or invent your own
2. Copy `templates/SKILL-TEMPLATE.md` to start
3. Fill in the sections
4. Test it with Claude Code
5. Iterate until it works reliably

## Exercises

### Beginner (15-20 min)
- [commit-message](exercises/01-commit-message/) — Generate conventional commits
- [explain-error](exercises/02-explain-error/) — Explain errors in plain English
- [meeting-prep](exercises/03-meeting-prep/) — Generate meeting agendas

### Intermediate (30-40 min)
- [changelog-generator](exercises/04-changelog/) — Git log → CHANGELOG
- [code-review](exercises/05-code-review/) — Structured code review

### Advanced (45-60 min)
- [retro-facilitator](exercises/06-retro/) — Guide sprint retrospectives

## Resources

- [Skill Template](templates/SKILL-TEMPLATE.md)
- [Example: Completed Skill](examples/commit-message/SKILL.md)
- [Tips & Best Practices](docs/BEST-PRACTICES.md)

## After the Workshop

Take your skills back to your projects! Skills can be:
- Project-specific (in your repo)
- Global (claude config)
- Claude desktop or web
- Team-shared (in a shared skills repo)

---

*Built for hands-on learning. Fork it, break it, make it yours.*
