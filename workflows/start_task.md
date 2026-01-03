---
description: Start Task (Branch Creation, Context Loading)
---

Execute this workflow to create a topic branch when starting a new feature or bug fix.

1. **Branch Naming**
   - Convention: `type/context`
     - Type: `feature`, `fix`, `docs`, `refactor`, `chore`
     - Context: Short English description (e.g., `link-fix`, `add-test`)
     - Example: `feature/image-optimization`, `fix/broken-link`

2. **Safety Check (Uncommitted Changes)**
   - [ ] Check for uncommitted changes. Stash or commit if any.
   // turbo
   git diff --quiet || echo "WARNING: Uncommitted changes detected. Please stash or commit them before proceeding."

3. **Script Check (Mental Check)**
   - [ ] Check `package.json` to understand available scripts (`lint`, `test`, `format`).

4. **Sync Main & Load Context**
   // turbo
   git checkout main && git pull origin main

   // turbo
   echo "Loading context..." && cat dev-docs/LESSONS.md dev-docs/TECH_STACK.md dev-docs/ARCHITECTURE.md dev-docs/DECISIONS.md README.md 2>/dev/null || echo "Some context files are missing, skipping."

5. **Create & Switch Branch**
   - [ ] Create and checkout the determined branch.
   // turbo
   git checkout -b <branch_name>