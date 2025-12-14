# epub2md Agent Configs

Private configuration repository for the AI Agent (Antigravity/Gemini) working on the [epub2md](https://github.com/mtskf/EPUB-to-Markdown-Converter) project.

This repository contains the persistent context, rules, and workflows that define the AI's persona and development process.

## 📂 Structure

- **`rules.md`**: The single source of truth for the AI's behavior. Contains:
  - Project Vision & Philosophy ("Zero manual edits")
  - Automation Rules (Trigger words for workflows)
  - Persona (Proactive Tech Lead, Japanese communication)
  - Development Guidelines (Test-first, Clean repo)
  
- **`workflows/`**: Automation scripts (Markdown definition) for common tasks.
  - `start_task.md`: Branch creation logic.
  - `finalize_task.md`: PR creation, testing, docs update logic.
  - `release.md`: Semantic versioning and GitHub Release automation.

## 🚀 Setup

To use these configs on a new machine:

```bash
# 1. Clone the main project
git clone https://github.com/mtskf/EPUB-to-Markdown-Converter.git
cd EPUB-to-Markdown-Converter

# 2. Clone this config repo into .agent/ (ignored by main repo)
git clone git@github.com:mtskf/epub2md-agent-configs.git .agent
```

## 🛡 Privacy
This repository is **Private**. It allows sharing the AI's "Secret Sauce" (custom prompts and contexts) across machines without exposing them in the public `epub2md` repository.
