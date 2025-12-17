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
- **Communication Style**:
  - 結果重視。定型句は排除。
  - 不確実な場合は、推測で進めずに `notify_user` で確認する。

## 2. エンジニアリング標準 (Engineering Standards)
- **Safety First (CRITICAL)**:
  - **Main Branch Protection**: `main` ブランチでの直接のファイル変更・作成・削除は **厳禁 (STRICTLY PROHIBITED)**。
  - 誤って `main` で作業しようとした場合は、直ちに中止し、ユーザーに報告するか `start_task` を促す。
  - ファイル操作前に `start_task` ワークフローが実行されているか確認。
  - 破壊的な操作 (delete, overwrite) は慎重に行う。
- **Testing & Quality**:
  - **Lint & Test**: コード変更後は必ず、`lint_and_test` ワークフローを実行して整合性を確認する。
  - 新機能にはテストを追加する。
- **Git**:
  - `main` への直コミット禁止。
  - コミットメッセージは Conventional Commits 形式。

## 3. 自動化ワークフロー (Automation Workflows)
以下のトリガーに応じて、`.agent/workflows/` 内の対応するワークフローを実行すること。

- **開始**: `start_task.md` (ブランチ作成、コンテキストロード)
- **完了**: `finalize_task.md` (PR作成、ドキュメントHygiene/Update、クリーンアップ)
- **同期**: `sync_main.md` (main同期、リモートPrune)
- **検証**: `lint_and_test.md` (Lint & Test実行)
- **リリース**: `release.md` (バージョンアップ、リリース)

## 4. Documentation
- **Keep it fresh**: コード変更に伴い、関連ドキュメント (`README.md`, `docs/`) を即座に更新する。
- **Artifacts**: ユーザーへの説明や計画には Artifacts を積極的に活用する。
- **Documentation Hygiene**:
  - `finalize_task` ワークフローの手順に従い、ドキュメントの最適化 (Optimization) とアーカイブ (Archiving) を毎回実施する。
