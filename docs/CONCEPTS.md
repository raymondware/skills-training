# Skills vs Commands vs Agents

Three ways to extend Claude Code — each for different situations.

## Quick Comparison

| | Skill | Command | Agent |
|---|-------|---------|-------|
| **What** | Instructions for how to do something | A specific action to trigger | An autonomous worker |
| **Trigger** | Automatic (pattern match) | Explicit (`/command`) | Spawned for a task |
| **Scope** | Single task workflow | One-shot action | Multi-step mission |
| **State** | Stateless | Stateless | Has own session/memory |
| **Complexity** | Low-Medium | Low | High |

---

## Skills

**What:** Reusable instruction sets that teach Claude how to handle specific tasks.

**File:** `SKILL.md`

**When to use:**
- Repetitive workflows you want standardized
- Team knowledge you want encoded
- Tasks with consistent patterns

**Examples:**
- Generate commit messages
- Review code with specific criteria
- Create meeting agendas

**How it works:**
1. Claude detects trigger phrase/context
2. Loads SKILL.md instructions
3. Follows the workflow
4. Produces formatted output

```markdown
# commit-message

Generate conventional commits from staged changes.

## Triggers
- "generate commit message"
- "commit this"

## Instructions
1. Run git diff --staged
2. Analyze changes
3. Output conventional commit format
```

**Pros:**
- Easy to create and share
- Automatic activation
- No infrastructure needed

**Cons:**
- No persistent state
- Can't run in background
- Single-conversation scope

---

## Commands

**What:** Explicit shortcuts that trigger specific actions.

**Syntax:** `/commandname [args]`

**When to use:**
- Frequent actions you want quick access to
- Actions that shouldn't trigger automatically
- Settings or mode changes

**Examples:**
- `/compact` — compress context
- `/clear` — reset conversation
- `/model sonnet` — switch models
- `/review src/` — kick off code review

**How it works:**
1. User types `/command`
2. Claude recognizes and executes
3. Immediate result

**Built-in Claude Code commands:**
- `/help` — show available commands
- `/compact` — reduce context size
- `/clear` — fresh start
- `/cost` — show token usage
- `/doctor` — check setup

**Custom commands** can be defined in CLAUDE.md or project config.

**Pros:**
- Explicit (no accidental triggers)
- Fast to invoke
- Good for actions, not workflows

**Cons:**
- Must remember command names
- Not discoverable without docs
- Limited to simple triggers

---

## Agents

**What:** Autonomous Claude instances that work independently on larger tasks.

**When to use:**
- Long-running tasks
- Parallel workstreams
- Tasks requiring isolation
- Background work while you do other things

**Examples:**
- "Research competitors and report back"
- "Refactor this module, I'll review when done"
- "Monitor this feed and alert me"
- Running multiple features in parallel

**How it works:**
1. Spawn agent with a task
2. Agent works in isolated session
3. Agent reports back when done
4. Can check on progress anytime

```bash
# Spawn a sub-agent
sessions_spawn task="Research top 5 competitors for X and summarize pricing"

# Check on running agents
sessions_list

# Get agent's work
sessions_history sessionKey="agent-123"
```

**Pros:**
- Parallel execution
- Isolated context (won't pollute main session)
- Can work while you're away
- Can coordinate multiple agents

**Cons:**
- More complex to set up
- Costs more tokens
- Requires orchestration for complex tasks
- State management needed

---

## Decision Tree

```
Need Claude to do something?
│
├─ Is it a quick, one-off action?
│  └─ YES → Just ask Claude directly
│
├─ Is it a repeatable workflow you want standardized?
│  └─ YES → Create a SKILL
│
├─ Is it something you want explicit control over (not auto-triggered)?
│  └─ YES → Create a COMMAND
│
├─ Is it a big task that should run in the background?
│  └─ YES → Spawn an AGENT
│
└─ Is it multiple parallel tasks?
   └─ YES → Spawn multiple AGENTS
```

---

## Combining Them

They work together:

1. **Command triggers Skill:**
   `/review` command loads the code-review skill

2. **Skill spawns Agents:**
   A "parallel-refactor" skill spawns agents for each module

3. **Agent uses Skills:**
   A research agent uses the "summarize" skill for each source

---

## Real-World Scenarios

### Scenario 1: Code Review
- **Just ask:** "Review this file" (one-off)
- **Skill:** Team has specific review criteria to enforce
- **Command:** `/review` for quick access
- **Agent:** Review 50 files in parallel

### Scenario 2: Documentation
- **Just ask:** "Document this function"
- **Skill:** "api-docs" skill for consistent format
- **Command:** `/docs generate`
- **Agent:** "Document the entire codebase, report when done"

### Scenario 3: Research
- **Just ask:** "What's the best React form library?"
- **Skill:** "tech-comparison" template
- **Agent:** "Research all options, test each, give me a recommendation"

---

## Summary

| Use Case | Solution |
|----------|----------|
| "I do this the same way every time" | Skill |
| "I want a quick shortcut" | Command |
| "Do this big thing while I'm away" | Agent |
| "I need consistent team processes" | Skill |
| "Run these 5 tasks in parallel" | Multiple Agents |
