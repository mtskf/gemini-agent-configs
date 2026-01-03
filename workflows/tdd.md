---
description: TDD Cycle (Red-Green-Refactor)
---

Follow this workflow when implementing features using Test-Driven Development.

1.  **Red: Write a Failing Test**
    - [ ] Create or update a test file (e.g., `test/my-feature.test.ts`).
    - [ ] Write a test case that describes the desired behavior.
    - [ ] Run the test watcher to confirm it fails.
    // turbo
    pnpm run test:watch

2.  **Green: Make it Pass**
    - [ ] Write the minimum amount of code to make the test pass.
    - [ ] Confirm the test passes in the watcher.

3.  **Refactor: Clean Up**
    - [ ] Improve code structure, readability, and performance without changing behavior.
    - [ ] Ensure tests still pass.
