---
description: Sync Main Branch & Cleanup
---

Workflow to update local environment after PR merge. Switches to `main`, pulls changes, removes old branches.

1. **Switch to Main & Update (with Prune & Submodule)**
   - [ ] Checkout `main`, fetch prune, pull, and update submodules.
   // turbo
   git checkout main && git fetch --prune origin && git pull origin main && git submodule update --init --recursive

2. **Update Dependencies**
   - [ ] Update package dependencies.
   // turbo
   pnpm install

3. **Delete Merged Branches (Optional)**
   - [ ] List and delete merged local branches (user confirmation recommended).
   - [ ] List merged branches.
   git branch --merged main | grep -v "^\*" | grep -v "main"
   - [ ] Delete merged branches.
   git branch --merged main | grep -v "^\*" | grep -v "main" | xargs -r git branch -d
