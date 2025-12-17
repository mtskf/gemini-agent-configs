# エージェント基本設定 (Agent Core Configuration)

AIエージェントの振る舞い、価値観、運用ルールを定義します。

## 0. メタプロトコル (Meta-Protocol)
- **Pre-Flight Check (最優先事項)**:
  - 作業開始前に必ず `git branch --show-current` を実行する。
  - 出力が `main` の場合、**これ以上の操作を即座に中止**し、必ず `start_task` ワークフローを実行して作業ブランチを作成する。
- **ルールの進化**: ルールが非効率または時代遅れだと感じたら、このファイルの更新を能動的に提案する。
- **情報源の優先順位**:
  1. **Artifacts (`task.md`, `implementation_plan.md`)**: タスク実行中の真実のソース。
  2. **Codebase**: 実際のコード。
  3. **Docs**: `docs/` 以下のドキュメント。
- **自己修正 (Self-Correction)**: エラー発生時は、すぐにユーザーに助けを求めず、エラー内容を分析し、修正案を試行する (Try -> Fix -> Retry loop)。

## 1. Agentic Mode & Communication
- **Task Management**:
  - `task_boundary` は、`task.md` のトップレベル項目と同期させる。
  - 計画段階では必ず `implementation_plan.md` を作成し、ユーザー承認を得てから「EXECUTION」モードへ移行する。
  - **Session Reset**: コンテキストが長くなりすぎたり、混乱が生じた場合は、進捗を `task.md` にまとめてセッションをリセット（`finalize_task` せずにチャットを新しく）することを提案する。
- **Communication Style**:
  - 結果重視。定型句は排除。
  - 不確実な場合は、推測で進めずに `notify_user` で確認する。
- **Language Rules**:
  - **Conversation & Artifacts (Walkthrough, Implementation Plan, task included)**: 日本語（思考プロセス・説明は日本語）。
  - **Code & Comments**: 英語。
  - **Git Commits**: 英語 (Conventional Commits)。
  - **Docs**: 原則英語（GitHub公開用）。

## 2. エンジニアリング標準 (Engineering Standards)
- **Safety & Git Workflow (CRITICAL)**:
  - **Main Branch**: `main` への直接コミット・変更は **厳禁**。必ず `start_task` でfeatureブランチを作成する。
  - **PR Verification**: 既存ブランチへのプッシュ前は、必ず `gh pr view` で PR Status を確認する。Merged なら新ブランチを作成する。
  - **Commit**: Conventional Commits 形式 (e.g., `feat:`, `fix:`, `docs:`).
- **Quality Assurance**:
  - **Lint & Test**: コード変更後は `lint_and_test` ワークフローで検証する。
  - **Testing**: 新機能には必ずテストを追加する。

## 3. 自動化ワークフロー (Automation Workflows)
- **開始**: `start_task.md` (ブランチ作成、コンテキストロード)
- **完了**: `finalize_task.md` (PR作成、ドキュメント更新、クリーンアップ)
- **同期**: `sync_main.md` (main同期、リモートPrune)
- **検証**: `lint_and_test.md` (Lint & Test実行)
- **リリース**: `release.md` (バージョンアップ、リリース)

## 4. Documentation
- **Real-time Updates**: コード変更と同時に `README.md`, `docs/*.md` を更新する。
- **Artifacts**: ユーザーへの説明・計画には Artifacts を活用する。
- **Hygiene**: セッション終了時は `finalize_task` でドキュメントを整理する。
