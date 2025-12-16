---
description: メインブランチの同期とクリーンアップ
---

PRマージ後にローカル環境を最新化するためのワークフローです。`main` ブランチに切り替え、Pullを行い、マージ済みの作業ブランチを削除するオプションを提供します。

1. **メインブランチへの切り替えと更新 (with Prune & Submodule)**
   - [ ] `main` ブランチにチェックアウトし、リモートの変更を取り込み、古いトラッキングブランチを削除する。
   // turbo
   git checkout main && git fetch --prune origin && git pull origin main && git submodule update --init --recursive

2. **依存関係の更新**
   - [ ] パッケージの依存関係を更新する。
   // turbo
   pnpm install

3. **マージ済みブランチの削除（オプション）**
   - [ ] マージ済みのローカルブランチを一覧表示し、削除する（ユーザー確認推奨）。
   // turbo
   git branch --merged main | grep -v "^\*" | grep -v "main" | xargs -r git branch -d
