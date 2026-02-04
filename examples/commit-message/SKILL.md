# Commit Message Generator

Generate conventional commit messages from staged changes.

## Triggers

Use this skill when the user:
- Asks to "generate a commit message"
- Says "commit this" or "write commit"
- Wants help with conventional commits

## Instructions

1. Run `git diff --staged` to see what's being committed
2. Analyze the changes:
   - What files changed?
   - What type of change? (feat/fix/docs/refactor/test/chore)
   - What's the scope? (component/module affected)
3. Generate a conventional commit message
4. If changes are complex, suggest breaking into multiple commits

## Output Format

```
<type>(<scope>): <short description>

<optional body explaining what and why>

<optional footer with breaking changes or issue refs>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation only
- `refactor`: Code change that neither fixes nor adds
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

## Examples

### Input
```
User: generate commit message
[staged: added login form component with validation]
```

### Output
```
feat(auth): add login form with validation

- Email and password fields with client-side validation
- Error states for invalid inputs
- Submit handler ready for API integration
```

### Input
```
User: commit this
[staged: fixed typo in README.md]
```

### Output
```
docs: fix typo in README
```

## Notes

- Keep the subject line under 72 characters
- Use imperative mood ("add" not "added")
- If changes span multiple concerns, suggest separate commits
