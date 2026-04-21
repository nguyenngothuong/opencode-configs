---
description: "Push to GitHub - create branch, push, and optionally create PR"
---

Follow these steps to push and optionally create a PR:

1. Run `git status` to check current state
2. If branch is not created yet:
   - Create branch: `git checkout -b <branch-name>`
   - Use conventional naming: `feat/feature-name`, `fix/issue-name`, `chore/task-name`
3. Push to remote: `git push -u origin <branch-name>`
4. Show the push result

If the user asks for a PR or wants one:
5. Run `gh pr create` with:
   - `--title` - Conventional title (same format as commit)
   - `--body` - Description of changes
   - `--base main` (or `master` if that's the default)
6. Show the PR URL

If user provides arguments ($ARGUMENTS):
- Use first argument as branch name
- Use remaining arguments as PR title/body context

Best practices:
- Always verify remote exists with `git remote -v`
- Use `-u` flag on first push to set upstream
- Handle authentication errors gracefully (user is logged in via gh CLI)
- Never force push unless explicitly requested
