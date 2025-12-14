---
description: タスク完了処理 (PR作成、ドキュメント更新)
---

このワークフローは、変更のコミットからプルリクエストの作成までを自動化します。

1. **ドキュメント更新**
   - [ ] `HISTORY.md` に変更内容を追記。
   - [ ] **機能追加・変更があった場合、`README.md` を更新する。**
   - [ ] アーキテクチャ変更があった場合、`ARCHITECTURE.md` を更新する。

2. **動作確認**
   - [ ] テスト実行。
   // turbo
   npm test

3. **コミット & プッシュ**
   - [ ] 現在のブランチ名を確認。
   - [ ] 変更をコミットし、リモートにプッシュする。
   // turbo
   git add . && git commit -m "<type>: <subject>" && git push origin HEAD

4. **プルリクエスト作成**
   - [ ] GitHub CLI で PR を作成する。タイトルと本文はコミット内容から生成させる。
   // turbo
   gh pr create --fill
