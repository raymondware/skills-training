# Walkthrough: Error Explainer

Build a skill that translates cryptic errors into plain English.

**Time:** 15-20 minutes

---

## Step 1: Create the File (1 min)

Create `SKILL.md` with the basics:

```markdown
# Error Explainer

Explain error messages in plain English with actionable fixes.
```

---

## Step 2: Define Triggers (2 min)

When should this skill activate?

```markdown
## Triggers

Use this skill when the user:
- Pastes an error message or stack trace
- Asks "what does this error mean"
- Says "explain this error"
- Asks for help debugging an error
```

---

## Step 3: Write Instructions (5 min)

```markdown
## Instructions

1. Identify the error type and language/framework
2. Find the root cause:
   - What operation failed?
   - What was the expected vs actual state?
3. Explain in plain English:
   - What happened (1 sentence)
   - Why it happened (context)
4. Provide actionable fixes:
   - List 1-3 ways to solve it
   - Include code examples when helpful
5. Mention prevention tips if relevant
```

---

## Step 4: Define Output Format (2 min)

```markdown
## Output Format

### ❌ Error
`[Original error message]`

### 💡 What Happened
[One sentence plain English explanation]

### 🔍 Why
[Context about what causes this]

### ✅ How to Fix

**Option 1:** [Fix description]
\`\`\`javascript
// code example
\`\`\`

**Option 2:** [Alternative fix]

### 🛡️ Prevention
[How to avoid this in the future]
```

---

## Step 5: Add Examples (5 min)

Show Claude how to handle different errors:

```markdown
## Examples

### Example 1: JavaScript undefined

**Input:**
\`\`\`
TypeError: Cannot read property 'map' of undefined
\`\`\`

**Output:**

### ❌ Error
`TypeError: Cannot read property 'map' of undefined`

### 💡 What Happened
You tried to call `.map()` on a variable that doesn't exist yet.

### 🔍 Why
The variable is `undefined` instead of being an array. This usually happens when:
- Data hasn't loaded yet (async issue)
- API returned unexpected shape
- Variable was never initialized

### ✅ How to Fix

**Option 1: Optional chaining**
\`\`\`javascript
items?.map(item => <Item key={item.id} {...item} />)
\`\`\`

**Option 2: Guard clause**
\`\`\`javascript
{items && items.map(item => ...)}
\`\`\`

**Option 3: Default value**
\`\`\`javascript
const items = data.items || [];
items.map(...)
\`\`\`

### 🛡️ Prevention
Initialize arrays with empty defaults and add loading states for async data.

---

### Example 2: Connection error

**Input:**
\`\`\`
Error: connect ECONNREFUSED 127.0.0.1:5432
\`\`\`

**Output:**

### ❌ Error
`ECONNREFUSED 127.0.0.1:5432`

### 💡 What Happened
Your app tried to connect to a database on port 5432, but nothing is listening there.

### 🔍 Why
Port 5432 is the default PostgreSQL port. The database server is either:
- Not running
- Running on a different port
- Blocked by firewall

### ✅ How to Fix

**Option 1: Start PostgreSQL**
\`\`\`bash
# macOS
brew services start postgresql

# Linux
sudo systemctl start postgresql

# Docker
docker start postgres-container
\`\`\`

**Option 2: Check connection string**
Verify your DATABASE_URL matches your actual setup.

### 🛡️ Prevention
Add database health checks to your startup sequence.
```

---

## Step 6: Handle Edge Cases (2 min)

```markdown
## Notes

- If the error is ambiguous, ask for more context (full stack trace, what triggered it)
- Detect language automatically when possible (Python tracebacks, JS errors, etc.)
- For unknown errors, still provide general debugging steps
- Link to official docs when relevant
```

---

## Step 7: Test It (3 min)

Try these errors:

1. `KeyError: 'username'` (Python)
2. `FATAL: password authentication failed for user "postgres"`
3. `SyntaxError: Unexpected token '<'`
4. A real error from your current project

Check:
- Did it explain clearly?
- Was the fix actionable?
- Did it detect the language?

---

## Final Skill

```markdown
# Error Explainer

Explain errors in plain English with actionable fixes.

## Triggers
- User pastes error/stack trace
- "what does this error mean"
- "explain this error"

## Instructions
1. Identify error type and language
2. Find root cause
3. Explain in plain English
4. Provide 1-3 fixes with code
5. Add prevention tip

## Output Format
[See above]

## Examples
[See above]

## Notes
- Ask for more context if ambiguous
- Auto-detect language
- Link to docs when helpful
```

---

## 🎉 Done!

You've built a skill that turns frustrating error messages into learning moments. This pattern (parse → explain → fix) works for many debugging scenarios.
