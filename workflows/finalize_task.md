---
description: タスク完了処理 (PR作成、ドキュメント更新)
---

このワークフローは、変更のコミットからプルリクエストの作成までを自動化します。

1. **ドキュメント更新 (Hygiene Check)**
   - [ ] `docs/CHANGELOG.md` の [Unreleased] セクションに変更内容を追記。
   - [ ] **Archiving**: `docs/CHANGELOG.md` が肥大化している場合は、古い内容を `docs/Archives/` へ移動する。
   - [ ] 重要な教訓があれば `docs/LESSONS.md` に抽出。
   - [ ] **Architecture**: `docs/ARCHITECTURE.md` を確認する。未作成の場合は現時点の設計で作成する。既存の場合は、差分だけでなく**現在のシステム全体の設計**を表すように更新する。
   - [ ] アーキテクチャ変更があれば `docs/DECISIONS.md` に ADR を追加。
   - [ ] 機能追加・変更があった場合、`README.md` を更新。
   - [ ] **Optimization**: `docs/LESSONS.md`, `docs/DECISIONS.md`, `docs/ARCHITECTURE.md` を見直し、重複・陳腐化した項目を整理（削除/統合/移動）する。

2. **動作確認**
    - [ ] テスト実行。
    // turbo
    pnpm test

3. **コミット & プッシュ**
   - [ ] 現在のブランチ名を確認。
   - [ ] 変更をコミットし、リモートにプッシュする。
   // turbo
   git add . && git commit -m "<type>: <subject>" && git push origin HEAD

4. **プルリクエスト作成**
   - [ ] **注意**: `push` が完全に完了するのを待ってから実行すること。
   - [ ] GitHub CLI で PR を作成する。タイトルと本文は英語で具体的に記述。
   // turbo
   gh pr create --title "feat: Add feature X" --body "Description of changes"
