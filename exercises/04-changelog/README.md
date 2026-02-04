# Exercise 4: Changelog Generator

**Difficulty:** Intermediate  
**Time:** 30-40 minutes

## Goal

Build a skill that reads git history and generates a formatted CHANGELOG entry.

## What You'll Learn

- Shell command integration
- Parsing git output
- Categorizing changes
- Markdown formatting

## Requirements

Your skill should:
1. Read git commits since last tag/release
2. Categorize by type (Added/Changed/Fixed/etc.)
3. Generate Keep a Changelog format
4. Handle both conventional and non-conventional commits

## Getting Started

1. Create `SKILL.md` in this folder
2. Useful commands:
   - `git log --oneline v1.0.0..HEAD`
   - `git describe --tags --abbrev=0`
   - `git log --pretty=format:"%s"`

## Output Format (Keep a Changelog)

```markdown
## [1.1.0] - 2024-01-15

### Added
- New feature description

### Changed
- Change description

### Fixed
- Bug fix description

### Removed
- Removed feature
```

## Test Cases

Given these commits:
```
feat: add dark mode toggle
fix: resolve login timeout issue
docs: update API documentation
refactor: simplify auth logic
```

Expected output categorizes each appropriately.

## Hints

<details>
<summary>Hint 1: Getting commits since last tag</summary>

```bash
LAST_TAG=$(git describe --tags --abbrev=0 2>/dev/null || echo "")
if [ -n "$LAST_TAG" ]; then
  git log $LAST_TAG..HEAD --oneline
else
  git log --oneline -20
fi
```

</details>

<details>
<summary>Hint 2: Mapping types to categories</summary>

- `feat` → Added
- `fix` → Fixed  
- `refactor`, `perf` → Changed
- `docs` → (often excluded or separate)
- `BREAKING CHANGE` → ⚠️ highlight

</details>

## Stretch Goals

- Auto-detect version bump (major/minor/patch)
- Link commits to PRs/issues
- Support multiple output formats (Keep a Changelog, GitHub releases)
