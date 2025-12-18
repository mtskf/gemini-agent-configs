---
description: タスク完了処理 (PR作成、ドキュメント更新)
---

このワークフローは、変更のコミットからプルリクエストの作成までを自動化します。

1. **ドキュメント更新 (Hygiene Check)**
   - [ ] `dev-docs/CHANGELOG.md` の [Unreleased] セクションに変更内容を追記。
   - [ ] **Archiving**: `dev-docs/CHANGELOG.md` が肥大化している場合は、古い内容を `dev-docs/Archives/` へ移動する。
   - [ ] 重要な教訓があれば `dev-docs/LESSONS.md` に抽出。
   - [ ] **Architecture**: `dev-docs/ARCHITECTURE.md` を確認する。未作成の場合は現時点の設計で作成する。既存の場合は、差分だけでなく**現在のシステム全体の設計**を表すように更新する。
   - [ ] アーキテクチャ変更があれば `dev-docs/DECISIONS.md` に ADR を追加。
   - [ ] 機能追加・変更があった場合、`README.md` を更新。
   - [ ] **Optimization**: `dev-docs/LESSONS.md`, `dev-docs/DECISIONS.md`, `dev-docs/ARCHITECTURE.md` を見直し、重複・陳腐化した項目を整理（削除/統合/移動）する。

2. **動作確認**
    - [ ] テスト実行。
    // turbo
    pnpm test

3. **コミット & プッシュ (with Verification)**
   - [ ] **Self-Check**: 以下の項目を自問自答する。
     - [ ] **Complexity**: Is the solution as simple as possible? (YAGNI/KISS)
     - [ ] **Naming**: Do variable/function names match `dev-docs/TECH_STACK.md` conventions?
     - [ ] **Hygiene**: Did I remove all `console.log` / debug comments?
     - [ ] **Context**: Does this change align with `dev-docs/ARCHITECTURE.md`?
     - [ ] **Tests**: Did I run existing tests (`pnpm test`) and pass?
     - [ ] **Docs**: Did I update `dev-docs/CHANGELOG.md` and other relevant docs?
   - [ ] **PR Status Check**: `gh pr view` で現在のブランチに関連するPRが既にマージされていないか確認する。Mergedなら新ブランチを作成。
   - [ ] **Self-Review**: `git diff --cached` で最終確認。
   - [ ] 変更をコミットし、リモートにプッシュする。

   // turbo
   git add . && git commit -m "<type>: <subject>" && git push origin HEAD

4. **プルリクエスト作成**
   - [ ] **注意**: `push` が完全に完了するのを待ってから実行すること。
   - [ ] GitHub CLI で PR を作成する。タイトルと本文は英語で具体的に記述。
   // turbo
   gh pr create --title "feat: Add feature X" --body "Description of changes"