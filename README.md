# epub2md エージェント設定
[epub2md](https://github.com/mtskf/EPUB-to-Markdown-Converter) プロジェクトで活動する AIエージェント (Antigravity/Gemini) のためのプライベート設定リポジトリです。

このリポジトリには、AIのペルソナや開発プロセスを定義する永続的なコンテキスト、ルール、ワークフローが含まれています。

## 📂 構造

- **`rules.md`**: AIの振る舞いを決定する唯一の正解 (SSOT)。以下を含みます：
  - プロジェクトのビジョンと哲学 ("Zero manual edits")
  - 自動化ルール (ワークフローのトリガーワード)
  - ペルソナ (Proactive Tech Lead, 日本語でのコミュニケーション)
  - 開発ガイドライン (テストファースト, クリーンなリポジトリ)

- **`workflows/`**: 共通タスクのための自動化スクリプト (Markdown定義)。
  - `start_task.md`: ブランチ作成ロジック
  - `finalize_task.md`: PR作成、テスト、ドキュメント更新ロジック
  - `release.md`: セマンティックバージョニングとGitHubリリース自動化

## 🚀 セットアップ

新しいマシンでこれらの設定を使用するには：

```bash
# 1. メインプロジェクトをクローン
git clone https://github.com/mtskf/EPUB-to-Markdown-Converter.git
cd EPUB-to-Markdown-Converter

# 2. この設定リポジトリを .agent/ にクローン (メインリポジトリからは無視されます)
git clone git@github.com:mtskf/epub2md-agent-configs.git .agent
```

## 🛡 プライバシー
このリポジトリは **Private** です。AIの「秘伝のタレ」（カスタムプロンプトやコンテキスト）を公開 `epub2md` リポジトリに晒すことなく、複数のマシン間で共有することを可能にします。
