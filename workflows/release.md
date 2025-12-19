---
description: Release Workflow (Version Bump, Tagging, GitHub Release)
---

Workflow for project release. Execute this when requested to "release" or "bump version".

1.  **Determine Version**
    - Confirm with user or judge from changes.
    - `patch`: Bug fixes, docs updates
    - `minor`: New features
    - `major`: Breaking changes

2.  **Update `package.json` & Tag**
    - [ ] Run `npm/pnpm version` command.
    // turbo
    pnpm version <type> -m "Release: v%s"

3.  **Build & Package**
    - [ ] Build the project and create a release package in `release/` folder.

4.  **Push to Remote**
    - [ ] Push commit and tags.
    // turbo
    git push origin main --follow-tags

5.  **Create GitHub Release**
    - [ ] Generate release notes from pushed tag and upload the package from `release/` folder.
    // turbo
    gh release create v<new_version> release/* --generate-notes
