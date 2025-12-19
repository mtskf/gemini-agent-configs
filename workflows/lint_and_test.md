---
description: Lint and Test (Quality Check)
---

Workflow to ensure code quality after changes. Executes `lint` and `test` scripts defined in `package.json`.

1. **Run Lint**
   - [ ] Check if `lint` script exists in `package.json` and run it.
   // turbo
   if grep -q '"lint":' package.json; then pnpm run lint; else echo "No lint script found."; fi

2. **Run Test**
   - [ ] Check if `test` script exists in `package.json` and run it.
   // turbo
   if grep -q '"test":' package.json; then pnpm run test; else echo "No test script found."; fi
