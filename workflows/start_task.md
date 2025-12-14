---
description: タスク開始処理 (ブランチ作成)
---

新しい機能開発やバグ修正を開始するときは、必ずこのワークフローを実行してトピックブランチを作成します。

1. **ブランチ名の決定**
   - 命名規則: `type/context`
     - Type: `feature`, `fix`, `docs`, `refactor`, `chore`
     - Context: 作業内容を表す短い英語 (例: `link-fix`, `add-test`)
     - 例: `feature/image-optimization`, `fix/broken-link`

2. **最新の main を取得**
   // turbo
   git checkout main && git pull origin main

3. **ブランチの作成と移動**
   - [ ] 決定したブランチ名で作成・移動する。
   // turbo
   git checkout -b <branch_name>
