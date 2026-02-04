# Walkthrough: Changelog Generator

Build a skill that turns git history into formatted release notes.

**Time:** 30-40 minutes

---

## Step 1: Understand the Problem (3 min)

What we're building:
- Read git commits since the last release
- Categorize them (Added, Changed, Fixed, etc.)
- Output in Keep a Changelog format

Key commands you'll need:
```bash
# Get last tag
git describe --tags --abbrev=0

# Get commits since tag
git log v1.0.0..HEAD --oneline

# Get commit details
git log --pretty=format:"%s" v1.0.0..HEAD
```

---

## Step 2: Create the File (2 min)

```markdown
# Changelog Generator

Generate formatted CHANGELOG entries from git history.
```

---

## Step 3: Define Triggers (2 min)

```markdown
## Triggers

Use this skill when the user:
- Asks to "generate changelog"
- Wants "release notes"
- Says "what changed since last release"
- Asks to "update CHANGELOG"
```

---

## Step 4: Write Instructions (10 min)

This is more complex — handle multiple scenarios:

```markdown
## Instructions

1. **Find the baseline:**
   \`\`\`bash
   git describe --tags --abbrev=0 2>/dev/null
   \`\`\`
   - If tag exists: use it as baseline
   - If no tags: use last 20 commits or ask user

2. **Get commits since baseline:**
   \`\`\`bash
   git log [baseline]..HEAD --pretty=format:"%s"
   \`\`\`

3. **Categorize each commit:**

   | Commit prefix | Category |
   |---------------|----------|
   | `feat:` | Added |
   | `fix:` | Fixed |
   | `refactor:`, `perf:` | Changed |
   | `docs:` | Documentation (or exclude) |
   | `BREAKING CHANGE` | ⚠️ Breaking |
   | Other | Changed (default) |

4. **Group by category and format**

5. **Suggest version bump:**
   - Breaking changes → MAJOR
   - New features → MINOR
   - Bug fixes only → PATCH

6. **Output in Keep a Changelog format**
```

---

## Step 5: Define Output Format (3 min)

```markdown
## Output Format

\`\`\`markdown
## [X.Y.Z] - YYYY-MM-DD

### ⚠️ Breaking Changes
- Description of breaking change

### Added
- New feature description
- Another new feature

### Changed
- Change description

### Fixed
- Bug fix description

### Removed
- Removed feature description
\`\`\`

**Notes:**
- Empty categories should be omitted
- Most recent/important items first
- Link to PRs/issues if commit messages include them
```

---

## Step 6: Add Examples (10 min)

```markdown
## Examples

### Example 1: Feature release

**Input:**
\`\`\`
User: generate changelog
Last tag: v1.2.0
Commits since tag:
  feat: add dark mode toggle
  feat(auth): implement OAuth login
  fix: resolve race condition in data fetch
  fix: correct timezone handling in scheduler
  docs: update API documentation
  refactor: simplify user service
\`\`\`

**Output:**

## [1.3.0] - 2024-01-15

### Added
- Add dark mode toggle
- Implement OAuth login for authentication

### Changed
- Simplify user service internals

### Fixed
- Resolve race condition in data fetch
- Correct timezone handling in scheduler

**Suggested version:** 1.3.0 (MINOR - new features, no breaking changes)

---

### Example 2: Breaking change release

**Input:**
\`\`\`
User: what changed since v2.0.0
Commits:
  feat!: redesign API response format
  BREAKING CHANGE: removed deprecated endpoints
  feat: add batch processing
  fix: memory leak in worker pool
\`\`\`

**Output:**

## [3.0.0] - 2024-01-15

### ⚠️ Breaking Changes
- **API Response Format:** Response structure has changed. See migration guide.
- **Deprecated Endpoints Removed:** `/v1/users` and `/v1/legacy/*` no longer available

### Added
- Batch processing support for bulk operations

### Fixed
- Memory leak in worker pool

**Suggested version:** 3.0.0 (MAJOR - breaking changes)

---

### Example 3: No tags exist

**Input:**
\`\`\`
User: generate changelog
(no git tags found)
\`\`\`

**Output:**

No git tags found. Options:
1. Generate changelog from last 20 commits
2. Specify a commit hash as baseline: "changelog since abc123"
3. Create initial tag first: `git tag v0.1.0`

Which would you prefer?
```

---

## Step 7: Handle Edge Cases (3 min)

```markdown
## Notes

- If no tags exist, ask user for baseline or use commit count
- Non-conventional commits: categorize as "Changed" or ask
- Merge commits: typically skip unless they have meaningful messages
- If > 50 commits, summarize by category rather than listing all
- Commits with multiple types: use the primary one or mention in description
```

---

## Step 8: Test It (5 min)

In a real git repo:

1. Check you have tags: `git tag`
2. Run: "generate changelog"
3. Verify:
   - Categories are correct
   - Nothing important is missing
   - Format matches Keep a Changelog
   - Version suggestion makes sense

Edge cases to try:
- Repo with no tags
- Only `chore:` and `docs:` commits
- Commits with breaking changes

---

## 🎉 Done!

This skill combines:
- Shell command execution
- Text parsing and categorization
- Structured output formatting

It's a great example of taking tedious manual work and automating it consistently.
