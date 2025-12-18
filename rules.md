# Agent Rules

## ⛔ BEFORE ANY CODE CHANGE - MANDATORY CHECK

```bash
git branch --show-current
```

- **If output is `main`** → STOP immediately → Run `/start_task` workflow
- **If output is feature branch** → Proceed with work

> **This check is NON-NEGOTIABLE. No exceptions. Ever.**

---

## Git Workflow (CRITICAL)

| Action | Rule |
|--------|------|
| Direct push to `main` | ❌ FORBIDDEN |
| Work on `main` branch | ❌ FORBIDDEN |
| Create feature branch | ✅ Use `/start_task` |
| Before push to existing branch | ✅ Run `gh pr view` to check status |
| Commit format | ✅ Conventional Commits (`feat:`, `fix:`, `docs:`) |

---

## Communication

- **Language**: Conversation in 日本語, Code/Commits/Docs in English
- **Style**: Result-focused, no filler phrases
- **Uncertainty**: Use `notify_user` instead of guessing

## Engineering

- **Quality**: Run build after changes, verify before push
- **Docs**: Update README/dev-docs with code changes
- **Artifacts**: Use `task.md`, `implementation_plan.md` for planning

## Workflows

| Workflow | Purpose |
|----------|---------|
| `/start_task` | Create branch, load context |
| `/finalize_task` | Create PR, cleanup |
| `/sync_main` | Sync with remote main |
