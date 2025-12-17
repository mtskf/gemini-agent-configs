---
description: タスク開始処理 (ブランチ作成、コンテキスト読み込み)
---

新しい機能開発やバグ修正を開始するときは、必ずこのワークフローを実行してトピックブランチを作成します。

1. **ブランチ名の決定**
   - 命名規則: `type/context`
     - Type: `feature`, `fix`, `docs`, `refactor`, `chore`
     - Context: 作業内容を表す短い英語 (例: `link-fix`, `add-test`)
     - 例: `feature/image-optimization`, `fix/broken-link`

2. **安全確認 (Uncommitted Changes)**
   - [ ] コミットされていない変更がないか確認する。変更がある場合は stash するかコミットする。
   // turbo
   git diff --quiet || echo "WARNING: Uncommitted changes detected. Please stash or commit them before proceeding."

3. **スクリプト確認 (Mental Check)**
   - [ ] `package.json` を確認し、利用可能なスクリプト (`lint`, `test`, `format`) を把握する。
   - [ ] 必要なスクリプトが不足している場合は、タスクの一環として追加を検討する。

4. **最新の main を取得**
   // turbo
   git checkout main && git pull origin main

4. **コンテキストのロード (Auto-Load & Verify)**
   - [ ] **Automated Load**: 以下の重要ドキュメントを読み込み、コンテキストに入れる。
     - `docs/LESSONS.md` (教訓)
     - `docs/TECH_STACK.md` (技術スタック)
     - `docs/ARCHITECTURE.md` (アーキテクチャ)
     - `docs/DECISIONS.md` (ADR)
     - `README.md` (基本情報)
   // turbo
   cat docs/LESSONS.md docs/TECH_STACK.md docs/ARCHITECTURE.md docs/DECISIONS.md README.md 2>/dev/null || echo "Docs check skipped or partial."

5. **ブランチの作成と移動**
   - [ ] 決定したブランチ名で作成・移動する。
   // turbo
   git checkout -b <branch_name>