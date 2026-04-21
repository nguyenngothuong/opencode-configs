---
description: "Smart commit - analyze changes, stage, and commit with conventional message"
---

Follow these steps to create a clean commit:

1. Run `git status` and `git diff --stat` to understand changes
2. Categorize changes by type (feat, fix, refactor, docs, chore, test, etc.)
3. Stage files logically using `git add` (group related changes)
4. Create a conventional commit message:
   - Format: `type(scope): description`
   - Body explains WHAT and WHY (not HOW)
   - Max 72 chars for subject line
   - Use imperative mood ("fix" not "fixed")
5. Run `git commit -m "message"`
6. Show the commit hash and summary

If nothing to commit, say "Working tree clean - nothing to commit."

Common types:
- feat: new feature
- fix: bug fix
- refactor: code restructuring (no behavior change)
- docs: documentation
- test: tests
- chore: maintenance/config changes
- perf: performance improvements
- style: formatting/whitespace only
