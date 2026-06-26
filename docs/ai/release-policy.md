# Release Policy

## 公開フロー

`main` へ push すると GitHub Actions（`.github/workflows/publish.yml`）が `npx @vscode/vsce publish` で VS Code Marketplace へ自動公開する。

公開には Actions シークレット `VSCE_PAT`（Azure DevOps の PAT / Marketplace = Manage スコープ）を使用する。

## バージョンポリシー

- テーマの色調整など軽微な変更: パッチアップ。
- テーマ追加など: マイナーアップ。
- 同じ `package.json` version は Marketplace に再公開できないため、変更のたびに必ず version を上げる。

## publisher の責務

`publisher` は commit / push までを担当する。ビルドやテストは存在しないため実行しない。

標準フロー:

1. `git status -sb`
2. `git diff --stat`
3. `package.json` の version が変更内容に合っていることを確認
4. 必要な変更だけ stage
5. commit
6. push
