# AIエージェント設定 (AI Agent Configuration)

AIエージェント (Antigravity/Gemini) のためのプライベート設定リポジトリです。
プロジェクトのルートディレクトリに `.agent/` として配置し、AIのペルソナ、運用ルール、ワークフローを定義します。

## 📂 構造

- **`rules.md`**: **エージェントの行動規範 (Generic Rules)**。
  - **Meta-Protocol**: Pre-Flight Check (ブランチ確認), 自己修正 (Self-Correction)。
  - **Agentic Mode**: タスク管理, Artifacts 活用。
  - **Engineering Standards**: 安全第一 (Main Branch 保護), Lint & Test。
  - **Documentation Hygiene**: 最適化 & アーカイブ。

- **`workflows/`**: **自動化ワークフロー**。
  - `start_task.md`: タスク開始 (ブランチ作成, コンテキスト, スクリプト確認)
  - `finalize_task.md`: タスク完了 (PR作成, ドキュメント整理, クリーンアップ)
  - `sync_main.md`: 同期 (Main Pull, Prune, Submodule)
  - `lint_and_test.md`: 品質チェック (Lint, Test)
  - `release.md`: リリース手順

## � 管理対象ドキュメント (Managed Documentation)
利用側のプロジェクト (`docs/`) で自動的に管理・更新されるドキュメント群です。`finalize_task` ワークフローで最適化されます。

- **`docs/ARCHITECTURE.md`**: 現在のシステム全体の設計図 (Living Document)。差分ではなく**今の状態**を記述します。
- **`docs/CHANGELOG.md`**: ユーザー向けの変更履歴。[Unreleased] に追記され、肥大化すると `docs/Archives/` に移動されます。
- **`docs/DECISIONS.md`**: アーキテクチャ決定記録 (ADR)。重要な技術的決定を記録します。
- **`docs/LESSONS.md`**: プロジェクトを通じて得られた教訓やベストプラクティス。

## �🚀 セットアップ

任意のプロジェクトで、この設定リポジトリを `.agent/` ディレクトリとして利用します。

```bash
# プロジェクトのルートディレクトリで実行
git clone <URL_TO_THIS_REPO> .agent
```

**⚠️ 重要:**
フォルダ名は必ず **`.agent`** に変更してください（git clone 時に指定するか、clone 後にリネームしてください）。Antigravity は `.agent` ディレクトリ内の設定を自動的に読み込みます。

## 🛡 プライバシー & コンセプト
このディレクトリ (`.agent/`) は、通常 `.gitignore` に含まれ、メインのプロジェクトリポジトリにはコミットされません（またはプライベートなサブモジュールとして管理されます）。
これにより、AIの「秘伝のタレ」（カスタムプロンプト、運用ノウハウ、個別ルール）を公開リポジトリと分離して管理・共有できます。
