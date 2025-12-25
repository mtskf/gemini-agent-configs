# AI Agent Configuration

Configuration repository to transform Google Antigravity / Gemini from a simple coder into a **"Proactive Tech Lead"**.

By placing this as an `.agent/` directory at the project root, you provide the AI with a "Project Cortex" consisting of **Rules of Conduct (Rules)** and **Autonomous Development Cycles (Workflows)**.
This prevents context loss, eliminates `main` branch accidents, and keeps documentation and code in sync.

Reference: [Antigravity x Gemini を "Proactive Tech Lead" に育てる試みとその記録 #AI - Qiita](https://qiita.com/gurigurico/items/fa2bb68dde57042490d2) (Japanese)

## 📂 Structure

- **`rules.md`**: **Agent's Rules of Conduct (Generic Rules)**.
  - **Meta-Protocol**: Pre-Flight Check (branch verification), Self-Correction.
  - **Agentic Mode**: Task management, Artifact usage.
  - **Engineering Standards**: Safety First (Main Branch protection), Lint & Test, Image Asset Rules.
  - **Documentation Hygiene**: Optimization & Archiving.

- **`workflows/`**: **Automation Workflows**.
  - `start_task.md`: Start Task (Create branch, Load context, Check scripts)
  - `finalize_task.md`: Complete Task (Create PR, Update docs, Cleanup)
  - `sync_main.md`: Sync (Pull Main, Prune, Submodules)
  - `lint_and_test.md`: Quality Check (Lint, Test)
  - `release.md`: Release Procedure (Version bump, Tagging)

## 📝 Managed Documentation

These documents reside in `dev-docs/` and are automatically managed and updated by the agent. They are optimized via the `finalize_task` workflow.

- **`dev-docs/ARCHITECTURE.md`**: The system's blueprint (Living Document). Describes the **current state**, not just diffs.
- **`dev-docs/CHANGELOG.md`**: User-facing change history. Appended to `[Unreleased]`. Old entries are moved to `dev-docs/Archives/` to prevent bloating.
- **`dev-docs/DECISIONS.md`**: Architecture Decision Records (ADR). Records important technical decisions.
- **`dev-docs/LESSONS.md`**: Lessons learned and best practices.

## 🚀 Setup

Use this configuration repository as the `.agent/` directory in any project.

```bash
# Execute at project root
git clone https://github.com/mtskf/gemini-agent-configs.git .agent

# Add .agent directory to gitignore (Recommended)
echo ".agent/" >> .gitignore
```

**⚠️ IMPORTANT:**
Ensure the folder name is **`.agent`**. Antigravity automatically reads configurations from this specific directory.

## 🛡 Privacy & Concept

It is **strongly recommended** to add `.agent/` to `.gitignore` and **NOT** commit it to the main project repository (or manage it as a private submodule).
This allows you to decouple and manage your "AI Secret Sauce" (custom prompts, operational know-how, unique rules) separately from public repositories.

## 🔧 Advanced Setup

### Symbolic Link
If you work across multiple projects, you can use symbolic links to centralize your configuration.

```bash
# Clone config repo to a central location
git clone https://github.com/mtskf/gemini-agent-configs.git ~/Dev/AI/gemini-agent-configs

# Create link at project root
ln -s ~/Dev/AI/gemini-agent-configs .agent

# Add to .gitignore
echo ".agent" >> .gitignore
```

**⚠️ Warning**:
Symbolic links are best for individual local environments. For team development or shared repositories, `git submodule` is recommended to avoid broken links on other machines.

## 📚 References
- [Antigravity x Geminiを "Proactive Tech Lead" に育てる試みとその記録 #AI - Qiita](https://qiita.com/gurigurico/items/fa2bb68dde57042490d2)
