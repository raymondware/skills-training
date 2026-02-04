# Walkthrough: Commit Message Generator

A step-by-step guide to building your first skill.

**Time:** 15-20 minutes

---

## Step 1: Create the File (2 min)

Create a new file called `SKILL.md` in this folder.

Start with the basic structure:

```markdown
# Commit Message Generator

Generate conventional commit messages from staged changes.
```

**✅ Checkpoint:** You have a file with a title and description.

---

## Step 2: Define Triggers (3 min)

Think about: *When should Claude use this skill?*

Add a Triggers section:

```markdown
## Triggers

Use this skill when the user:
- Asks to "generate a commit message"
- Says "commit this" or "write commit"
- Wants help with conventional commits
```

**Tips:**
- Be specific enough to avoid false triggers
- Include common phrasings people actually use
- Think about context (user has staged changes)

**✅ Checkpoint:** You've defined 2-3 clear trigger conditions.

---

## Step 3: Write Instructions (5 min)

This is the core of your skill. Tell Claude exactly what to do.

```markdown
## Instructions

1. Run `git diff --staged` to see what's being committed
2. Analyze the changes:
   - What files changed?
   - What type of change? (feat/fix/docs/refactor/test/chore)
   - What's the scope? (component or module affected)
3. Generate a conventional commit message
4. If changes are complex, suggest breaking into multiple commits
```

**Tips:**
- Number your steps
- Be specific about commands to run
- Include decision points (what type of change?)
- Handle edge cases (complex changes → split suggestion)

**✅ Checkpoint:** Claude knows what to do step-by-step.

---

## Step 4: Define Output Format (3 min)

Show Claude exactly what the output should look like:

```markdown
## Output Format

\`\`\`
<type>(<scope>): <short description>

<optional body explaining what and why>

<optional footer with breaking changes or issue refs>
\`\`\`

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation only
- `refactor`: Code change that neither fixes nor adds
- `test`: Adding or updating tests
- `chore`: Maintenance tasks
```

**Tips:**
- Use code blocks to show exact format
- Include all valid options (types list)
- Note what's optional vs required

**✅ Checkpoint:** Output format is crystal clear.

---

## Step 5: Add Examples (5 min)

Examples are the secret sauce. Show input → output pairs:

```markdown
## Examples

### Example 1: Simple change
**Input:**
\`\`\`
User: generate commit message
[staged: fixed typo in README.md]
\`\`\`

**Output:**
\`\`\`
docs: fix typo in README
\`\`\`

### Example 2: Feature addition
**Input:**
\`\`\`
User: commit this
[staged: added login form component with validation]
\`\`\`

**Output:**
\`\`\`
feat(auth): add login form with validation

- Email and password fields with client-side validation
- Error states for invalid inputs
- Submit handler ready for API integration
\`\`\`
```

**Tips:**
- Include simple AND complex examples
- Show the variety of outputs possible
- Make examples realistic

**✅ Checkpoint:** You have 2+ examples showing different scenarios.

---

## Step 6: Handle Edge Cases (2 min)

What could go wrong? Tell Claude how to handle it:

```markdown
## Notes

- Keep the subject line under 72 characters
- Use imperative mood ("add" not "added")
- If no staged changes, prompt user to stage files first
- If changes span multiple concerns, suggest separate commits
```

**✅ Checkpoint:** Edge cases are covered.

---

## Step 7: Test It! (5 min)

Now try your skill:

1. Stage some changes in a git repo:
   ```bash
   git add some-file.js
   ```

2. Ask Claude:
   ```
   generate a commit message for my staged changes
   ```

3. Check the output:
   - Does it follow conventional commit format?
   - Is the type correct?
   - Is the description accurate?

4. Try edge cases:
   - Multiple unrelated changes
   - No staged changes
   - Very large changeset

**✅ Checkpoint:** Skill works for typical and edge cases.

---

## Final SKILL.md

Your completed skill should look something like this:

```markdown
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
   - What's the scope? (component or module affected)
3. Generate a conventional commit message
4. If changes are complex, suggest breaking into multiple commits

## Output Format

\`\`\`
<type>(<scope>): <short description>

<optional body explaining what and why>
\`\`\`

**Types:** feat | fix | docs | refactor | test | chore

## Examples

### Simple
Input: User staged a README typo fix
Output: `docs: fix typo in README`

### Complex
Input: User staged a new login form
Output:
\`\`\`
feat(auth): add login form with validation

- Email and password fields
- Client-side validation
- Error state handling
\`\`\`

## Notes

- Subject line under 72 characters
- Imperative mood ("add" not "added")
- Suggest splitting if changes span multiple concerns
```

---

## 🎉 Congratulations!

You've built your first skill. The pattern is always the same:

1. **Triggers** — when to activate
2. **Instructions** — what to do
3. **Output Format** — what it looks like
4. **Examples** — show don't tell
5. **Notes** — handle edge cases

Now try the next exercise or create your own skill!
