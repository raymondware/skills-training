# Skill Building Best Practices

## 1. Start Simple, Iterate

Don't try to handle every edge case in v1. Build the happy path first, then expand.

```
v1: Basic functionality
v2: Handle edge cases  
v3: Add advanced features
```

## 2. Write Clear Triggers

Claude needs to know when to use your skill. Be specific:

**❌ Vague:**
```markdown
## Triggers
Use for code stuff
```

**✅ Specific:**
```markdown
## Triggers
Use this skill when the user:
- Says "generate commit message" or "write commit"
- Asks for help with conventional commits
- Has staged changes and wants to commit
```

## 3. Give Examples

Examples are worth 1000 words of instruction. Show Claude what good output looks like:

```markdown
## Examples

### Input
User: explain this error
TypeError: Cannot read property 'map' of undefined

### Output
**What happened:** You tried to call `.map()` on something that doesn't exist.

**Why:** The variable you're mapping over is `undefined` instead of an array.

**Fix:** Check that your data is loaded before mapping:
\`\`\`javascript
{items && items.map(item => ...)}
// or
{items?.map(item => ...)}
\`\`\`
```

## 4. Structure Instructions as Steps

Numbered steps are easier to follow than paragraphs:

**❌ Wall of text:**
```markdown
First analyze the code then look for bugs and also check security and make sure to format the output nicely...
```

**✅ Clear steps:**
```markdown
1. Read the file or diff provided
2. Scan for critical issues (bugs, security)
3. Note style/readability suggestions
4. Format findings by severity
5. Include line numbers and fix suggestions
```

## 5. Define Output Format

Be explicit about what the output should look like:

```markdown
## Output Format

\`\`\`markdown
## Review: [filename]

### 🔴 Critical Issues
- **Line X:** [problem] → [fix]

### 🟡 Suggestions
- **Line X:** [suggestion]

### ✅ Verdict
[APPROVE / REQUEST CHANGES]
\`\`\`
```

## 6. Handle Edge Cases Gracefully

Tell Claude what to do when things aren't perfect:

```markdown
## Notes
- If no staged changes exist, prompt user to stage files first
- If changes are too large, summarize by file rather than line-by-line
- If commit type is ambiguous, ask for clarification
```

## 7. Keep Skills Focused

One skill = one job. Don't build a Swiss Army knife.

**❌ Too broad:**
"Git Helper" that does commits, branches, rebases, stashes...

**✅ Focused:**
- "commit-message" — generates commits
- "branch-name" — suggests branch names
- "pr-description" — writes PR descriptions

## 8. Test with Real Scenarios

Before shipping, test with:
- Typical use case
- Edge case (empty input, huge input)
- Ambiguous input (does Claude ask for clarification?)
- Wrong context (does Claude know NOT to use the skill?)

## 9. Version Your Skills

As you improve skills, track what changed:

```markdown
## Changelog
- v1.0: Initial release
- v1.1: Added support for breaking changes
- v1.2: Better handling of multi-file commits
```

## 10. Share and Learn

- Review other skills for patterns
- Share what works with your team
- Publish useful skills to ClawdHub

---

## Common Pitfalls

| Pitfall | Solution |
|---------|----------|
| Too vague | Add specific examples |
| Too rigid | Allow for variations |
| No error handling | Add "what if" notes |
| Huge scope | Split into multiple skills |
| No testing | Try edge cases before shipping |

## Skill Quality Checklist

- [ ] Triggers are specific and accurate
- [ ] Instructions are numbered steps
- [ ] Output format is clearly defined
- [ ] At least one example included
- [ ] Edge cases are handled
- [ ] Tested with real inputs
