---
description: Task Completion (PR Creation, Documentation Update)
---

This workflow automates the process from committing changes to creating a Pull Request.

1. **Documentation Update (Hygiene Check)**
   - [ ] **Changelog**: Add changes to the `[Unreleased]` section in `dev-docs/CHANGELOG.md`.
   - [ ] **Archiving**: If `dev-docs/CHANGELOG.md` is too large, move old entries to `dev-docs/Archives/`.
   - [ ] **Lessons**: Extract important lessons to `dev-docs/LESSONS.md`.
   - [ ] **Architecture**: Check `dev-docs/ARCHITECTURE.md`. Create if missing. Update to reflect the **current system design**.
   - [ ] **Specs**: Check `dev-docs/SPEC.md`. Create if missing. Update to reflect **current functional specifications**.
   - [ ] **Decisions**: Add ADR to `dev-docs/DECISIONS.md` if architectural changes were made.
   - [ ] **Readme**: Update `README.md` if new features were added or modified.
   - [ ] **Consistency Check**: Verify that `.env`, `.env.example`, `GUIDE.md`, and `SPEC.md` are synchronized regarding configuration variables.
   - [ ] **Optimization**: Review `dev-docs/LESSONS.md`, `dev-docs/DECISIONS.md`, and `dev-docs/ARCHITECTURE.md` to remove or merge obsolete items.

2. **Quality Check**
   - [ ] Run linting if available.
   // turbo
   if grep -q '"lint":' package.json; then pnpm run lint; else echo "No lint script found."; fi
   - [ ] Run tests. **Abort immediately** if tests fail.
   // turbo
   pnpm test || exit 1

3. **Commit & Push (with Verification)**
   - [ ] **Self-Check**: Ask yourself:
     - [ ] **Complexity**: Is the solution as simple as possible? (YAGNI/KISS)
     - [ ] **Naming**: Do variable/function names match `dev-docs/TECH_STACK.md` conventions?
     - [ ] **Hygiene**: Did I remove all `console.log` / debug comments?
     - [ ] **Context**: Does this change align with `dev-docs/ARCHITECTURE.md`?
     - [ ] **Tests**: Did I run existing tests (`pnpm test`) and pass?
     - [ ] **Docs**: Did I update `dev-docs/CHANGELOG.md` and other relevant docs?
   - [ ] **PR Status Check**: Run `gh pr view` to ensure no merged PR exists for this branch. If merged, create a new branch.
   - [ ] **Self-Review**: Run `git diff --cached` for a final check.
   - [ ] Commit and push to remote.

   // turbo
   git add . && git commit -m "<type>: <subject>" && git push origin HEAD

4. **Create Pull Request**
   - [ ] **WAIT**: Ensure the push is completely finished.
   - [ ] Create PR using GitHub CLI. Write title and body in **English**.
   // turbo
   gh pr create --title "feat: Add feature X" --body "Description of changes"