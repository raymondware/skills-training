# Walkthrough: Code Review

Build a skill that performs structured, actionable code reviews.

**Time:** 30-40 minutes

---

## Step 1: Understand the Problem (3 min)

A good code review:
- Finds real issues, not just style nitpicks
- Prioritizes by severity
- Suggests fixes, not just problems
- Acknowledges what's done well
- Is actionable and specific

What we're NOT building: a linter. Focus on things humans catch.

---

## Step 2: Create the File (2 min)

```markdown
# Code Review

Perform structured code reviews with prioritized, actionable feedback.
```

---

## Step 3: Define Triggers (2 min)

```markdown
## Triggers

Use this skill when the user:
- Asks to "review this code"
- Wants a "code review" of a file or PR
- Says "check this for issues"
- Asks "what's wrong with this code"
```

---

## Step 4: Write Instructions (10 min)

Define what to look for and how to prioritize:

```markdown
## Instructions

1. **Read the code** (file path, diff, or pasted code)

2. **Scan for critical issues first:**
   - Bugs that will break in production
   - Security vulnerabilities
   - Data loss risks
   - Race conditions

3. **Then check for improvements:**
   - Performance issues
   - Error handling gaps
   - Edge cases not covered
   - Unclear logic

4. **Note readability concerns:**
   - Confusing naming
   - Missing comments on complex logic
   - Functions that are too long
   - Dead code

5. **Identify what's done well:**
   - Good patterns used
   - Clean structure
   - Thoughtful error handling

6. **Format findings by severity with line numbers**

7. **Give overall verdict:**
   - APPROVE: Ship it
   - APPROVE WITH SUGGESTIONS: Ship it, minor things to consider
   - REQUEST CHANGES: Fix these before merging
```

---

## Step 5: Define Output Format (3 min)

```markdown
## Output Format

\`\`\`markdown
## Code Review: [filename or PR]

### Summary
[1-2 sentence overview of the code and review findings]

### 🔴 Critical (Must Fix)
- **Line X:** [Issue description]
  → [Suggested fix with code if helpful]

### 🟡 Suggestions (Should Consider)
- **Line X:** [Issue description]
  → [Suggested improvement]

### 🟢 Looks Good
- [Positive observation about the code]

### Verdict: [APPROVE / APPROVE WITH SUGGESTIONS / REQUEST CHANGES]
[Brief rationale]
\`\`\`
```

---

## Step 6: Add Examples (10 min)

```markdown
## Examples

### Example 1: Security issue found

**Input:**
\`\`\`javascript
// auth.js
async function login(req, res) {
  const { username, password } = req.body;
  const query = `SELECT * FROM users WHERE username = '${username}' AND password = '${password}'`;
  const user = await db.query(query);
  if (user) {
    req.session.user = user;
    res.json({ success: true });
  }
}
\`\`\`

**Output:**

## Code Review: auth.js

### Summary
Authentication endpoint with critical SQL injection vulnerability and insecure password handling.

### 🔴 Critical (Must Fix)

- **Line 3:** SQL Injection vulnerability - user input directly concatenated into query
  → Use parameterized queries:
  \`\`\`javascript
  const query = 'SELECT * FROM users WHERE username = $1 AND password = $2';
  const user = await db.query(query, [username, password]);
  \`\`\`

- **Line 3:** Plain text password comparison - passwords should be hashed
  → Use bcrypt to compare:
  \`\`\`javascript
  const user = await db.query('SELECT * FROM users WHERE username = $1', [username]);
  if (user && await bcrypt.compare(password, user.password_hash)) {
    // valid login
  }
  \`\`\`

### 🟡 Suggestions

- **Line 5:** No rate limiting - vulnerable to brute force attacks
  → Add rate limiting middleware

- **Line 6:** Storing entire user object in session may include sensitive data
  → Store only necessary fields: `{ id: user.id, username: user.username }`

### 🟢 Looks Good
- Using async/await consistently
- Checking for user existence before setting session

### Verdict: REQUEST CHANGES
Critical security vulnerabilities must be fixed before this can be merged.

---

### Example 2: Clean code with minor suggestions

**Input:**
\`\`\`typescript
// useDebounce.ts
import { useState, useEffect } from 'react';

export function useDebounce<T>(value: T, delay: number): T {
  const [debouncedValue, setDebouncedValue] = useState<T>(value);

  useEffect(() => {
    const timer = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);

    return () => clearTimeout(timer);
  }, [value, delay]);

  return debouncedValue;
}
\`\`\`

**Output:**

## Code Review: useDebounce.ts

### Summary
Clean, well-typed debounce hook following React best practices.

### 🔴 Critical
None

### 🟡 Suggestions

- **Line 4:** Consider a default delay value for convenience
  → `export function useDebounce<T>(value: T, delay: number = 300): T`

- Consider adding JSDoc comment explaining usage:
  \`\`\`typescript
  /**
   * Debounce a value by the specified delay.
   * @param value - Value to debounce
   * @param delay - Delay in ms (default: 300)
   */
  \`\`\`

### 🟢 Looks Good
- Proper TypeScript generics
- Cleanup function prevents memory leaks
- Correct dependency array
- Single responsibility

### Verdict: APPROVE
Clean implementation, ship it! Suggestions are nice-to-haves.
```

---

## Step 7: Handle Edge Cases (3 min)

```markdown
## Notes

- If code is too large, focus on the most critical files or ask user to specify
- For PRs/diffs: focus on changed lines but consider surrounding context
- Don't nitpick style if there's a linter/formatter in the project
- If you need more context (what does this connect to?), ask
- For unfamiliar languages: note limitations, focus on universal issues
```

---

## Step 8: Test It (5 min)

Try reviewing:
1. A file from your current project
2. Some intentionally bad code
3. A recent PR diff

Verify:
- Severity ratings are accurate
- Line numbers are correct
- Suggestions are actionable (not vague)
- Tone is constructive

---

## 🎉 Done!

This skill turns code review from "I found 47 things" to "here are 3 things that matter, in order." The priority system is key — nobody wants to wade through nitpicks to find the security hole.
