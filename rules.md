# Agent Rules

## 🛡️ Core Protocols

1.  **Branch Safety**:
    *   **NEVER** modify `main` directly.
    *   **ALWAYS** check `git branch --show-current` before `write_to_file`/`replace_file_content`.
    *   If on `main`, STOP and run `/start_task`.
2.  **Implementation**:
    *   **NO** unrequested features/libraries. Focus strictly on the task.
    *   **PROPOSE** before implementing optimizations or fixes outside scope.
3.  **Communication**:
    *   Use **Japanese** for conversation/artifacts.
    *   Use **English** for code, commits, and documentation.
    *   Be concise: Result-focused, no filler.

## 📦 Engineering Standards

*   **Priority**: Artifacts (`task.md`) > Codebase > Docs.
*   **Quality**: Always run `/lint_and_test` after significant changes.
*   **Tests**: Add tests for new features. Fix test env issues in config, not source.
*   **Docs**: Keep `README.md` and `dev-docs/*` updated with code changes.
*   **Assets**: Store generated images in `temp/images/`.

## 🔄 Workflows

| Command | Purpose |
| :--- | :--- |
| `/start_task` | Create branch, load context. usage: `start_task.md` |
| `/finalize_task` | Create PR, cleanup. usage: `finalize_task.md` |
| `/sync_main` | Sync with remote main. usage: `sync_main.md` |
| `/lint_and_test` | Run lint & test. usage: `lint_and_test.md` |
| `/release` | Version bump & release. usage: `release.md` |
| `/tdd` | TDD cycle (Red-Green-Refactor). usage: `tdd.md` |

## 📚 References
*   `rules/coding-style.md`: Code style guidelines (Async, Error Handling, etc.)
*   `rules/image-gen.md`: Zero-shot prompting rules for Nano Banana.
*   `rules/testing.md`: Strict testing protocols (NO LIVE API calls).
