---
description: Lint and Test (Quality Check)
---

コード変更後に品質を担保するためのワークフローです。`package.json` に定義された `lint` および `test` スクリプトを実行します。

1. **Lint実行**
   - [ ] `package.json` に `lint` スクリプトがあるか確認し、あれば実行する。
   // turbo
   // turbo
   if grep -q '"lint":' package.json; then pnpm run lint; else echo "No lint script found."; fi

2. **Test実行**
   - [ ] `package.json` に `test` スクリプトがあるか確認し、あれば実行する。
   // turbo
   if grep -q '"test":' package.json; then pnpm run test; else echo "No test script found."; fi
