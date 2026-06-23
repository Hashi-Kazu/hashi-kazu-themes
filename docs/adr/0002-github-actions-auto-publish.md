# ADR-0002: GitHub Actions による main push 時自動公開

## ステータス
採用

## 確信度
高（コミット `27a768e` のメッセージ「Add Marketplace auto-publish workflow and metadata」および `.github/workflows/publish.yml` の内容から明確に確認できる）

## コンテキスト
VS Code Marketplace への公開には `vsce publish` コマンドと Azure DevOps PAT が必要であり、手動で実行するたびにローカル環境への PAT 設定が必要になる。
公開漏れや手順忘れのリスクがあり、継続的に新テーマを追加・更新する運用には自動化が望ましい。

## 決定
`main` ブランチへの push 時に GitHub Actions が自動で `npx @vscode/vsce publish` を実行し、VS Code Marketplace へ公開する。
ワークフローは `themes/**`・`package.json`・`README.md` の変更があった場合のみトリガーする（パスフィルター）。

## 理由
- ローカルへの PAT 設定が不要になり、任意の環境から `git push` だけで公開が完結する。
- パスフィルターにより、`CLAUDE.md` や `.gitattributes` だけを変更した push では無駄な公開ジョブが走らない。
- PAT はリポジトリの Actions シークレット `VSCE_PAT` に格納することでローカルに平文保管するリスクを排除できる。

## 捨てた選択肢
- **手動 `vsce publish`** → ローカルへの PAT 設定が必要で、公開手順を都度実行する運用コストがかかる。
- **Release タグをトリガーにする方式** → 調査時点で痕跡なし。push 直後に公開できるシンプルさを優先したと推測。

## 影響範囲
- `.github/workflows/publish.yml`：ワークフロー定義。トリガーパスの追加・変更はここで行う。
- `package.json` の `version`：同じバージョンは再公開不可。push 前に必ずバージョンを上げること（CLAUDE.md 参照）。
